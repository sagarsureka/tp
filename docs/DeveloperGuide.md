---
layout: page
title: Developer Guide
---

# Table of contents

* [1. Introduction](#1-introduction)
* [2. About this document](#2-about-this-document)
* [3. Setting up, getting started](#3-setting-up-getting-started)
* [4. Design](#4-design)
  * [4.1. Architecture](#41-architecture)
  * [4.2. UI component](#42-ui-component)
  * [4.3. Logic component](#43-logic-component)
  * [4.4. Model component](#44-model-component)
  * [4.5. Storage component](#45-storage-component)
  * [4.6. Common classes](#46-common-classes)
* [5. Implementation](#5-implementation)
  * [5.1. Undo/Redo feature](#51-undoredo-feature)
  * [5.2. Sort feature](#52-sort-feature)
  * [5.3. Quantity field in food items](#53-quantity-field-in-food-items)
  * [5.4. Change quantity feature](#54-change-quantity-feature)
  * [5.5. Find feature](#55-find-feature)
* [6. Documentation, logging, testing, configuration and dev-ops](#6-documentation-logging-testing-configuration-and-dev-ops)
* [Appendix A: Product scope](#appendix-a-product-scope)
* [Appendix B: Glossary](#appendix-b-glossary)
* [Appendix C: User stories](#appendix-c-user-stories)
* [Appendix D: Use cases](#appendix-d-use-cases)
  * [D.1. UC01: Add a food item](#d1-uc01-add-a-food-item)
  * [D.2. UC02: Delete a food item](#d2-uc02-delete-a-food-item)
  * [D.3. UC03: Edit a food item](#d3-uc03-edit-a-food-item)
  * [D.4. UC04: Change the quantity of a food item](#d4-uc04-change-the-quantity-of-a-food-item)
  * [D.5. UC05: Find a food item](#d5-uc05-find-a-food-item)
  * [D.6. UC06: List all food items](#d6-uc06-list-all-food-items)
  * [D.7. UC07: Clear all food items](#d7-uc07-clear-all-food-items)
  * [D.8. UC08: Sort food items by expiry date](#d8-uc08-sort-food-items-by-expiry-date)
  * [D.9. UC09: Sort food items by priority](#d9-uc09-sort-food-items-by-priority)
  * [D.10. UC10: Sort food items by description](#d10-uc10-sort-food-items-by-description)
  * [D.11. UC11: Undo most recent undoable command](#d11-uc11-undo-most-recent-undoable-command)
  * [D.12. UC12: Redo most recent undo command](#d12-uc12-redo-most-recent-undo-command)
* [Appendix E: Non-Functional requirements](#appendix-e-non-functional-requirements)
* [Appendix F: Instructions for manual testing](#appendix-f-instructions-for-manual-testing)
  * [F.1. Launch and shutdown](#f1-launch-and-shutdown)
  * [F.2. Deleting a food item](#f2-deleting-a-food-item)
  * [F.3. Changing the quantity of a food item](#f3-changing-the-quantity-of-a-food-item)
  * [F.4. Sorting the food list](#f4-sorting-the-food-list)
  * [F.5. Saving data](#f5-saving-data)
* [Appendix G: Effort](#appendix-g-effort)

--------------------------------------------------------------------------------------------------------------------

# 1. Introduction

SimplyKitchen is a desktop application for food inventory management suited for **household individuals who manage their kitchens' food items**.

SimplyKitchen is developed by 5 dedicated students who hope to assist and alleviate the problems you might encounter while managing your food inventory.
With intuitive and practical features, SimplyKitchen can get your food management tasks done faster and more efficiently!

With a Command Line Interface (CLI), SimplyKitchen is best suited to those who can type fast and prefer using a keyboard.
SimplyKitchen also uses a Graphical User Interface (GUI) to provide an aesthetic visualization of your food information for the ideal user experience.

SimplyKitchen hopes to empower you to work towards a **Tidy Kitchen, with Tiny Wastage**!

[Back to top](#table-of-contents)

--------------------------------------------------------------------------------------------------------------------

# 2. About this document

This document is a Developer Guide meant to assist project developers in understanding the various aspects in the production of SimplyKitchen.
The purpose of this document is to describe the architecture and software design decisions of SimplyKitchen.

The [Setting up, getting started](#3-setting-up-getting-started) section guides you in setting up the code base on your computer and helps you begin working on the project.

The [Design](#4-design) section helps you understand the design of the code base as a whole and its various components.
This section contains effective UML Diagrams which can help you understand the OOP structure of the code and the execution flow of the app.

The [Implementation](#5-implementation) section contains details about the implementation of some features in SimplyKitchen.
It also provides details about design considerations and implementation alternatives.
This section allows you to understand our thought process and make your own design considerations.

This is followed by a section consisting of guides for [Documentation, Logging, Testing, Configuration and DevOps](#6-documentation-logging-testing-configuration-and-dev-ops).
Each guide gives specific assistance in the context of the project.

<div style="page-break-after: always;"></div>

The [Appendix](#appendix-a-product-scope) section consists of details of the planning stage of the project.
It gives an idea of the requirements of the target audience of SimplyKitchen, along with use cases of how they will use the app.
The [Glossary](#appendix-b-glossary) and [Non-Functional Requirements](#appendix-e-non-functional-requirements) provide other key information relevant to the document and the app.

This document ends with a brief description of our [effort](#appendix-g-effort) for this project.

[Back to top](#table-of-contents)

--------------------------------------------------------------------------------------------------------------------

# 3. Setting up, getting started

Refer to the guide [_Setting up and getting started_](SettingUp.md).

[Back to top](#table-of-contents)

--------------------------------------------------------------------------------------------------------------------
<div style="page-break-after: always;"></div>

# 4. Design

## 4.1. Architecture

<img src="images/ArchitectureDiagram.png" width="450" />

The ***Architecture Diagram*** given above explains the high-level design of the App. Given below is a quick overview of each component.

<div markdown="span" class="alert alert-primary">

:bulb: **Tip:** The `.puml` files used to create diagrams in this document can be found in the [diagrams](https://github.com/AY2021S1-CS2103T-F13-4/tp/tree/master/docs/diagrams/) folder. Refer to the [_PlantUML Tutorial_ at se-edu/guides](https://se-education.org/guides/tutorials/plantUml.html) to learn how to create and edit diagrams.

</div>

**`Main`** has two classes called [`Main`](https://github.com/AY2021S1-CS2103T-F13-4/tp/blob/master/src/main/java/seedu/simplykitchen/Main.java) and [`MainApp`](https://github.com/AY2021S1-CS2103T-F13-4/tp/blob/master/src/main/java/seedu/simplykitchen/MainApp.java). It is responsible for,
* At app launch: Initializes the components in the correct sequence, and connects them up with each other.
* At shut down: Shuts down the components and invokes cleanup methods where necessary.
<div style="page-break-after: always;"></div>

[**`Commons`**](#46-common-classes) represents a collection of classes used by multiple other components.

The rest of the App consists of four components.

* [**`UI`**](#42-ui-component): The UI of the App.
* [**`Logic`**](#43-logic-component): The command executor.
* [**`Model`**](#44-model-component): Holds the data of the App in memory.
* [**`Storage`**](#45-storage-component): Reads data from, and writes data to, the hard disk.

Each of the four components,

* defines its *API* in an `interface` with the same name as the Component.
* exposes its functionality using a concrete `{Component Name}Manager` class (which implements the corresponding API `interface` mentioned in the previous point.

For example, the `Logic` component (see the class diagram given below) defines its API in the `Logic.java` interface and exposes its functionality using the `LogicManager.java` class which implements the `Logic` interface.

![Class Diagram of the Logic Component](images/LogicClassDiagram.png)

**How the architecture components interact with each other**

The *Sequence Diagram* below shows how the components interact with each other for the scenario where the user issues the command `delete 1`.

<img src="images/ArchitectureSequenceDiagram.png" width="574" />

The sections below give more details of each component.

[Back to top](#table-of-contents)

## 4.2. UI component

![Structure of the UI Component](images/UiClassDiagram.png)
<div style="page-break-after: always;"></div>

**API** :
[`Ui.java`](https://github.com/AY2021S1-CS2103T-F13-4/tp/blob/master/src/main/java/seedu/simplykitchen/ui/Ui.java)

The UI consists of a `MainWindow` that is made up of parts e.g.`CommandBox`, `ResultDisplay`, `FoodListPanel`, `StatusBarFooter`, `ExpiringFoodListPanel`, `ExpiredFoodListPanel` etc. All these, including the `MainWindow`, inherit from the abstract `UiPart` class.

The `UI` component uses JavaFx UI framework. The layout of these UI parts are defined in matching `.fxml` files that are in the `src/main/resources/view` folder. For example, the layout of the [`MainWindow`](https://github.com/AY2021S1-CS2103T-F13-4/tp/blob/master/src/main/java/seedu/simplykitchen/ui/MainWindow.java) is specified in [`MainWindow.fxml`](https://github.com/AY2021S1-CS2103T-F13-4/tp/blob/master/src/main/resources/view/MainWindow.fxml)

The `UI` component,

* Executes user commands using the `Logic` component.
* Listens for changes to `Model` data so that the UI can be updated with the modified data.

[Back to top](#table-of-contents)

## 4.3. Logic component

![Structure of the Logic Component](images/LogicClassDiagram.png)
<div style="page-break-after: always;"></div>

**API** :
[`Logic.java`](https://github.com/AY2021S1-CS2103T-F13-4/tp/blob/master/src/main/java/seedu/simplykitchen/logic/Logic.java)

1. `Logic` uses the `FoodInventoryParser` class to parse the user command.
1. This results in a `Command` object which is executed by the `LogicManager`.
1. The command execution can affect the `Model` (e.g. adding a food item).
1. The result of the command execution is encapsulated as a `CommandResult` object which is passed back to the `Ui`.
1. In addition, the `CommandResult` object can also instruct the `Ui` to perform certain actions, such as displaying help to the user.

Given below is the Sequence Diagram for interactions within the `Logic` component for the `execute("delete 1")` API call.

![Interactions Inside the Logic Component for the `delete 1` Command](images/DeleteSequenceDiagram.png)

<div markdown="span" class="alert alert-info">

**:information_source: Note:**<br>

The lifeline for `DeleteCommandParser` should end at the destroy marker (X) but due to a limitation of PlantUML, the lifeline reaches the end of diagram.

</div>

[Back to top](#table-of-contents)
<div style="page-break-after: always;"></div>

## 4.4. Model component

![Structure of the Model Component](images/ModelClassDiagram.png)

**API** : [`Model.java`](https://github.com/AY2021S1-CS2103T-F13-4/tp/blob/master/src/main/java/seedu/simplykitchen/model/Model.java)

The `Model`,

* stores a `UserPref` object that represents the user’s preferences.
* stores the food inventory data.
* exposes an unmodifiable `ObservableList<Food>` that can be 'observed' e.g. the UI can be bound to this list so that the UI automatically updates when the data in the list change.
* does not depend on any of the other three components.

<div markdown="span" class="alert alert-info">

**:information_source: Note:**<br>

An alternative (arguably, a more OOP) model is given below. It has a `Tag` list in the `FoodInventory`, which `Food` references. This allows `FoodInventory` to only require one `Tag` object per unique `Tag`, instead of each `Food` needing their own `Tag` object.

</div>

![BetterModelClassDiagram](images/BetterModelClassDiagram.png)

[Back to top](#table-of-contents)

## 4.5. Storage component

![Structure of the Storage Component](images/StorageClassDiagram.png)

**API** : [`Storage.java`](https://github.com/AY2021S1-CS2103T-F13-4/tp/blob/master/src/main/java/seedu/simplykitchen/storage/Storage.java)

The `Storage` component,
* can save `UserPref` objects in json format and read it back.
* can save the food inventory data in json format and read it back.

[Back to top](#table-of-contents)

## 4.6. Common classes

Classes used by multiple components are in the [`seedu.simplykitchen.commons`](https://github.com/AY2021S1-CS2103T-F13-4/tp/tree/master/src/main/java/seedu/simplykitchen/commons) package.

[Back to top](#table-of-contents)

--------------------------------------------------------------------------------------------------------------------
<div style="page-break-after: always;"></div>

# 5. Implementation

This section describes some noteworthy details on how certain features are implemented.

## 5.1. Undo/Redo feature

### Implementation

The feature is implemented with a `VersionedFoodInventory`. The `VersionedFoodInventory` contains the different states of the food inventory. The states are stored in a `foodInventoryStateList` and the current state is tracked with a `currentStatePointer`. It also implements the following methods:

* `VersionedFoodInventory#commit()` — Saves the current food inventory state in its states list.
* `VersionedFoodInventory#undo()` — Restores the previous food inventory state from its states list.
* `VersionedFoodInventory#redo()` — Restores a previously undone food inventory state from its states list.

These operations are exposed in the `Model` interface as `Model#commitFoodInventory()`, `Model#undoFoodInventory()` and `Model#redoFoodInventory()` respectively.

Given below is an example usage scenario and how the undo/redo mechanism behaves at each step.

Step 1. The user launches the application for the first time. The `VersionedFoodInventory` will be initialized with the initial food inventory state, and the `currentStatePointer` pointing to that single food inventory state.

![UndoRedoState0](images/UndoRedoState0.png)

Step 2. The user executes `delete 5` command to delete the 5th food item in the food inventory. The `delete` command calls `Model#commitFoodInventory()`, causing the modified state of the food inventory after the `delete 5` command executes to be saved in the `foodInventoryStateList`, and the `currentStatePointer` is shifted to the newly inserted food inventory state.

![UndoRedoState1](images/UndoRedoState1.png)

Step 3. The user executes `add d/Donut …​` to add a new food item. The `add` command also calls `Model#commitFoodInventory()`, causing another modified food inventory state to be saved into the `foodInventoryStateList`.

![UndoRedoState2](images/UndoRedoState2.png)

<div markdown="span" class="alert alert-info">

**:information_source: Note:**<br>

If a command fails its execution, it will not call `Model#commitFoodInventory()`, so the food inventory state will not be saved into the `foodInventoryStateList`.

</div>

Step 4. The user now decides that adding the food item was a mistake, and decides to undo that action by executing the `undo` command. The `undo` command will call `Model#undoFoodInventory()`, which will shift the `currentStatePointer` once to the left, pointing it to the previous food inventory state, and restores the food inventory to that state.

![UndoRedoState3](images/UndoRedoState3.png)
<div style="page-break-after: always;"></div>

<div markdown="span" class="alert alert-info">

**:information_source: Note:**<br>

If the `currentStatePointer` is at index 0, pointing to the initial food inventory state, then there are no previous food inventory states to restore. The `undo` command uses `Model#canUndoFoodInventory()` to check if this is the case. If so, it will return an error to the user rather than attempting to perform the undo.

</div>

The following sequence diagram shows how the undo operation works:

![UndoSequenceDiagram](images/UndoSequenceDiagram.png)

<div markdown="span" class="alert alert-info">

**:information_source: Note:**<br>

The lifeline for `UndoCommand` should end at the destroy marker (X) but due to a limitation of PlantUML, the lifeline reaches the end of diagram.

</div>

The `redo` command does the opposite — it calls `Model#redoFoodInventory()`, which shifts the `currentStatePointer` once to the right, pointing to the previously undone state, and restores the food inventory to that state.

<div markdown="span" class="alert alert-info">

**:information_source: Note:**<br>

If the `currentStatePointer` is at index `foodInventoryStateList.size() - 1`, pointing to the latest food inventory state, then there are no undone food inventory states to restore. The `redo` command uses `Model#canRedoFoodInventory()` to check if this is the case. If so, it will return an error to the user rather than attempting to perform the redo.

</div>

Step 5. The user then decides to execute the command `list`. Commands that do not modify the food inventory, such as `list`, will usually not call `Model#commitFoodInventory()`, `Model#undoFoodInventory()` or `Model#redoFoodInventory()`. Thus, the `foodInventoryStateList` remains unchanged.
<div style="page-break-after: always;"></div>

![UndoRedoState4](images/UndoRedoState4.png)

Step 6. The user executes `clear`, which calls `Model#commitFoodInventory()`. Since the `currentStatePointer` is not pointing at the end of the `foodInventoryStateList`, all food inventory states after the `currentStatePointer` will be purged. Reason: It no longer makes sense to redo the `add d/Donut …​` command.

![UndoRedoState5](images/UndoRedoState5.png)

The following activity diagram summarizes what happens when a user executes a new command:

![CommitActivityDiagram](images/CommitActivityDiagram.png)
<div style="page-break-after: always;"></div>
### Design consideration:

#### Aspect: How undo & redo executes

* **Alternative 1 (current choice):** Saves the entire food inventory.
  * Pros: Easy to implement.
  * Cons: May have performance issues in terms of memory usage.

* **Alternative 2:** Individual command knows how to undo/redo by
  itself.
  * Pros: Will use less memory (e.g. for `delete`, just save the food item being deleted).
  * Cons: We must ensure that the implementation of each individual command are correct.

[Back to top](#table-of-contents)

## 5.2. Sort feature
The sort feature allows users to sort the list of food items based on description, expiry date and priority.

### Implementation

The sort feature consists of three commands, `SortDescCommand`, `SortExpiryCommand` and `SortPriorityCommand` which extend `Command`.

The sorting order is in accordance to what is likely the most useful order for the user.

* `SortDescCommand` sorts the list of food by description, with items of the same description sorted by expiry date from oldest to newest, 
and items of the same description and expiry date sorted by priority from `HIGH` to `LOW`.

* `SortExpiryCommand` sorts the list of food by expiry date from oldest to newest, with items of the same expiry date sorted by priority from `HIGH` to `LOW`, 
and items of the same expiry date and priority sorted by description.

* `SortPriorityCommand` sorts the list of food by priority from `HIGH` to `LOW`, with items of the same priority sorted by expiry date from oldest to newest, 
and items of the same priority and expiry date sorted by description.

When the sort commands are executed by calling `SortDescCommand#execute(Model model)` or `SortExpiryCommand#execute(Model model)` or `SortPriorityCommand#execute(Model model)`, 
the `VersionedFoodInventory` attribute in `model` is sorted, which hence permanently sorts the `ObservableList<Food>` attribute in `UniqueFoodList`.
<div style="page-break-after: always;"></div>
This is done so by calling `model#sortFoodInventory(Comparator<Food>... comparators)` method in `model` which takes in a variable number of relevant `comparators` in order to sort the food list.

Following which, `model#setSortingComparators(Comparator<Food>[] sortingComparators)` and `userPref#setSortingComparatorsDescription(String sortingComparatorsDescription)` 
are called to save the sorting information in the user's `preferences.json` file. 

When invalid sorting information is read from `preferences.json` file, an error message will be displayed in the Result Box of the GUI, and the stored sorting order will be set to the default sorting: by description.

Sorting of the `VersionedFoodInventory` attribute in `model` is reflected in the GUI dynamically when `MainWindow` calls `logic#getFilteredFoodList()`.

The following sequence diagram illustrates how the command `sortdesc` works:

![SortDescSequenceDiagram](images/SortDescSequenceDiagram.png)

### Design consideration:

Comparators used for sorting are stored as static variables in `ComparatorUtil`, allowing for the code to be scalable for future sorting orders and commands.

Sorting information is stored as user preferences, to allow for the information to be retained when the application closes. Thus, the user's preferred sorting mechanism is stored, to enhance user experience.

Furthermore, this allows for dynamic updates of the food item list according to the stored sorting preference. In other words,
 when a food item is added or edited by calling `AddCommand` and `EditCommand`, the food item will be sorted dynamically according to the stored sorting mechanism. Thus, there is reduced hassle as the user does not need to sort the list again.
<div style="page-break-after: always;"></div>
#### Aspect: Permanence of list sorting

* **Alternative 1 (current choice):** Permanently sort lists.
  * Pros: There is less hassle when refreshing the app, as the specific sorting order preferred by the user is stored.
  * Cons: If the user wishes to sort displayed lists temporarily, they may only achieve this by sorting, then undoing the command, which may be a hassle.
* **Alternative 2:** Lists are always sorted by description by default, and sorting by priority or expiry date are reflected in displayed lists temporarily.
  * Pros: The user is able to sort the lists temporarily if they prefer to do so.<div style="page-break-after: always;"></div>
  * Cons: Sorting is not permanent, thus lists stored are sorted by description by default, which is not desirable if the user has other preferred sorting orders.

[Back to top](#table-of-contents)

## 5.3. Quantity field in food items

A `quantity` field for food items is implemented to track the dynamic changes in the quantity of a food in the FoodInventory.

### Implementation:

The `quantity` field has been implemented as a class in the `model.food` package.

* Quantity class contains 2 attributes: `value` and `unit`.
* The `value` is a positive number with a maximum of 2 decimal places. The maximum value allowed is 100,000.00.
* The `unit` is optional. If provided, it must consist of only alphabets. Numbers, space and special characters are not permitted.
* If the unit is not provided, a default unit - `unit` - will be given.
<div style="page-break-after: always;"></div>
### Implementation rationale:

The constraints above have been applied after careful consideration of the needs of the target audience.

* The `value` in the quantity field must be a positive value. A negative or zero value does not carry any meaning and would defeat the purpose of the feature.
* The maximum `value` allowed is 100,000.00. This value is chosen to accommodate users storing the volume of liquids they have in their kitchens.
  * Any value bigger than 100,000.00 is not realistic in the context of a domestic household.
* Users would want to track the quantity precisely in some cases. To allow this, SimplyKitchen accepts decimal values as the `value` attribute.
* The `value` attribute in the Quantity field has been stored as a `double` value.
* Users will have different kinds of units while tracking the quantity of their food items. For example, kg, can, bottle etc.
* To ensure the user's freedom in choosing the unit, the `unit` attribute in the Quantity class has been stored as a `String` field.
* Constraints on the content of the `unit` field have been applied to prevent misuse of the feature.
* Units are always single words and do not contain special characters or numbers. Hence, these restrictions have been enforced while accepting a quantity from the user.
* The `unit` field is optional to relieve the user of extra work of giving a unit in intuitive cases. For example, while storing the quantity of fish a unit is intuitively the number of fish.

### Design consideration:

#### Aspect: Implementation

* **Alternative 1 (current choice):** Value and unit stored as double and string fields in the Quantity class.
    * Pros: Easy to implement given the tight project timeframe.
    * Cons: Less OOP compared to the other alternative.
* **Alternative 2:** Value and Unit extracted to different classes. Quantity class' attributes are objects of these Value and Unit classes.
    * Pros: Improves OOP aspect of the code.
    * Cons: Unnecessarily complicates the code.

[Back to top](#table-of-contents)
<div style="page-break-after: always;"></div>

## 5.4. Change quantity feature

The change quantity feature allows users to increment or decrement the quantity of a food item by a certain amount.

### Implementation:

The `ChangeQuantityCommandParser` class parses the command by first extracting the index of the food item within the food list displayed to the user.

Next, the `amount` is parsed. It is a non-zero signed double value.
Similar to the constraints applied to the `quantity` field, the magnitude of the `amount` should be more than -100,000.00 and less than +100,000.00 but not zero.

* Having a `quantity` change of zero is meaningless.
* The signed value is used to denote the increment or decrement of the `quantity` value.
* The `amount` value is constrained to a maximum of 2 decimal places. Any additional decimal places used will not be meaningful from the user's point of view.
* A unit is not required as it can be derived from the existing unit of the food item when the user wants to change its `quantity`.

A new `ChangeQuantityCommand` object is created with the extracted index and `amount`. It will retrieve the correct food item from the filtered list of food item provided by the `model` object.

The selected food item will have its quantity updated through the `changeQuantityCommand#updateFoodQuantity` method.
The method will calculate the new `quantity` and throw a `CommandException` if the new `quantity` is less than or equal to zero, or more than 100,000.00.

* The `oldQuantity#updateQuantityValue` method is called within the `changeQuantityCommand#updateFoodQuantity` method.
* In the `updateQuantityValue` method, `BigDecimal` is used to do arithmetic operations on the old quantity's value and the `amount` to be incremented/decremented by. This is due to accuracy errors when performing arithmetic operations on double values.
<div style="page-break-after: always;"></div>
The following sequence diagram illustrates how the command `changeqty` works:

![ChangeqtySequenceDiagram](images/ChangeqtySequenceDiagram.png)

### Design consideration:

Although the `quantity` of a food item can be changed using the `edit` command, the command will replace the old `quantity` value with a value supplied by the user.
This means that users have to calculate the `quantity` themselves and calculation errors may occur as a result.
To minimise such errors and improve the intuitiveness of commands, the `changeqty` command allows users to specify **how much the quantity should change by**.
This allows users to not be burdened by calculations and to focus more on having an accurate inventory stock level.

#### Aspect: Updating a food item's quantity

* **Alternative 1 (current choice):** Update the `quantity` value of a food item by calling the `updateQuantityValue` method of the `Quantity` class.
    * Pros: Easy to implement given the tight project time frame.
    * Cons: All other fields of a `food` object need to be extracted and passed into the `Food` constructor.
* **Alternative 2:** Use a `Descriptor` class similar to the `EditFoodDescriptor` in the `EditCommand` class.
    * Pros: Improves OOP aspect of the code.
    * Cons: Unnecessarily complicates the code.
    * Cons: Only the `quantity` field of a `food` object is changed so a `Descriptor` class may be an overkill.

[Back to top](#table-of-contents)

## 5.5. Find feature

The find feature allows users to search for food items based on `description`, `expiry date`, `priority` and/or `tags`.

### Implementation:

The find feature is achieved by setting a `predicate` on the `filteredList` located in `ModelManager`. This can be done using the method `ModelManager#updateFilteredFoodList(Predicate<Food> predicate)`, which uses the parameter as the `predicate`. There are four valid predicates, namely `DescriptionContainsKeywordsPredicate`, `ExpirySearchPredicate`, `PrioritySearchPredicate` and `TagSearchPredicate`, all of which implement the `Predicate<Food>` interface. Based on the user's `find` command, each of the `predicate` is generated with the relevant search parameters. Then, the `FindCommand#combinePredicates()` method will combine all the predicates into a single `predicate` and is passed to `ModelManager#updateFilteredFoodList(Predicate<Food> predicate)`.

The following sequence diagram illustrates how the command `find d/apple e/30-9-2020 p/medium t/frozen` works:

![FindSequenceDiagram](images/FindSequenceDiagram.png)

The `find` command uses `ArgumentMultimap` to get the parameters of each `prefix`, similar to the `add` command. The `find` command needs to have at least one `prefix` present. If a `prefix` is present, then its respective `predicate` will be generated.

The following is the class diagram for the Find feature:

![FindClasseDiagram](images/FindClassDiagram.png)

### Implementation rationale:

Since the user can search for food items based on either the `description`, `expiry date`, `priority` or `tags`, the `find` command should allow searching for one or more of the above combination. This increases the flexibility in the `find` command, which allows the user to define the specificity of their search.

### Design consideration:

Each parameter of the search can be mapped to a `predicate`. This allows for scalability in the future as when a new attribute is added to `Food`, a new `predicate` implementing the `Predicate<Food>` interface can be created to search for this field without affecting the `predicates` of the other attributes.

#### Aspect: Implementation

* <b>Alternative 1 (current choice): </b> The `expiry date` in the `find` command looks for a single specific `expiry date`.
    * Pros: Easy to implement and search is more specific.
    * Cons: If the user wants to get all the expiring food items in a certain period, multiple searches will be required.
* <b>Alternative 2: </b> The `expiry date` in the `find` command can be a date range.
    * Pros: Able to get all the food items that are going to expire in a certain period with one search.
    * Cons: Will need more validation to ensure the date range provided is valid.

[Back to top](#table-of-contents)

--------------------------------------------------------------------------------------------------------------------

# 6. Documentation, logging, testing, configuration and dev-ops

* [Documentation guide](Documentation.md)
* [Testing guide](Testing.md)
* [Logging guide](Logging.md)
* [Configuration guide](Configuration.md)
* [DevOps guide](DevOps.md)

[Back to top](#table-of-contents)

--------------------------------------------------------------------------------------------------------------------

# Appendix A: Product scope

**Target user profile**:

* has a need to manage kitchen food items
* prefer desktop apps over other types
* prefers typing to mouse interactions
* can type fast
* is reasonably comfortable using CLI apps


**Value proposition**: With SimplyKitchen, food inventory management is made easy.

[Back to top](#table-of-contents)
<div style="page-break-after: always;"></div>

# Appendix B: Glossary

Term | Definition/Description
-----|------------------
**CLI** | Command Line Interface. It is a form of user and computer interaction where the user inputs commands in the form of text. Users will utilise a CLI to input commands into SimplyKitchen.
**Description** | The description of a food item.
**Expiring food item** | A food item is "expiring" if its expiry date is from today, to 7 days after today. For instance, if today is 7-11-2020, food items that expire from 7-11-2020 to 14-11-2020 are deemed as "expiring".
**Expiry date** | The expiry date of a food item.
**Food inventory** | A complete list of food items stored in Simply Kitchen.
**GUI** | Graphical User Interface. It is a form of user and computer interaction that allows the user to interact via graphical icons such as buttons, scroll bars and windows. SimplyKitchen has a GUI for the user to interact with.
**Mainstream OS** | Windows, Linux, Unix, OS-X.
**Priority** | The priority of a food item. The priority field can either be `high`, `medium` or `low`.
**Quantity** | The quantity of a food item. The quantity consists of 2 entities - `value` and `unit`.
**Tag** | Tags are additional information that can be tagged to food items.

[Back to top](#table-of-contents)
<div style="page-break-after: always;"></div>

# Appendix C: User stories

Priorities: High (must have) - `* * *`, Medium (nice to have) - `* *`, Low (unlikely to have) - `*`

| Priority | User role (As a …)                        | Function (I want to …)                                     | Benefit (So that I can …)                                                |
| -------- | ----------------------------------------- | ---------------------------------------------------------  | ------------------------------------------------------------------------ |
| `* * *`  | user                                      | add food items                                             |                                                                          |
| `* * *`  | user                                      | delete food items                                          |                                                                          |
| `* * *`  | user                                      | edit the fields of a food item                             | change the details of the food item after adding it                      |
| `* * *`  | user                                      | search for food items based on keywords of the description | find them easily                                                         |
| `* * *`  | user                                      | view a list of all food items I have added                 | have a complete display of all my food items                             |
| `* * *`  | user                                      | clear all food items                                       |                                                                          |
| `* * *`  | user who cares about some food items more | have different priority for different food items           | prioritise some food items                                               |
| `* * *`  | user                                      | use more intuitive commands                                | be more comfortable with using the app                                   |
| `* * *`  | user who likes efficiency                 | search for food items based on their priorities            | know which food items belong to a certain priority                       |
| `* * *`  | user                                      | search for food items based on their expiry dates          | know which food items are expiring on a certain date                     |
| `* * *`  | busy user                                 | sort my list of food items by their priorities             | know which food items are of certain priorities                          |
| `* * *`  | busy user                                 | sort my list of food items by their expiry dates           | know which food items are expiring first                                 |
| `* * *`  | busy user                                 | sort my list of food items by their description            | view a systematic list of food items sorted by description               |
| `* * *`  | busy user                                 | store my current sorting order                             | refresh the app while maintaining my current sorting order               |
| `* * *`  | user                                      | update the quantity of food items when I use them          | have an updated record of food items available in my kitchen             |
| `* * *`  | forgetful user                            | be able to view a list of expired food items               | know which food items are expired and can be thrown away                 |
| `* * *`  | forgetful user                            | be able to view a list of expiring food items              | know which food items are expiring soon and use them before they expired |
| `* * *`  | user                                      | undo and redo my actions                                   | easily fix the mistakes when using the application                       |
| `* *`    | user                                      | tag food items                                             | add additional information pertaining/relating to them                   |
| `* *`    | user                                      | search for food items based on their tags                  | know which food items are tagged with a certain information              |
| `*`      | user                                      | see some sample data populated in the app                  | understand how the app will look like and what benefits it has           |

[Back to top](#table-of-contents)

# Appendix D: Use cases

For all use cases, the **System** is SimplyKitchen, and the **Actor** is the User, unless otherwise specified.

## D.1. UC01: Add a food item

**Guarantees:** The food item is added into the food inventory.

**MSS:**

**1.**  User requests to add a food item.

**2.**  SimplyKitchen adds the food item to the food inventory and displays a success message.

Use case ends.

**Extensions:**

**1a.** SimplyKitchen detects an error in the user's food item.

 * **1a1.** SimplyKitchen displays an error message and prompts the user to enter a correct food item.

 * **1a2.** User enters another food item.

   Steps **1a1.** - **1a2.** are repeated until the food item entered is correct.

   Use case resumes from step **2**.

<br/>

## D.2. UC02: Delete a food item

**Precondition:** The food item to be deleted is currently in the food inventory.

**Guarantees:** If a food item is specified, the food item will be deleted from the food inventory.

**MSS:**

**1.** User requests to <ins>find a food item (UC05)</ins> or <ins>list all food items (UC06)</ins>.

**2.** SimplyKitchen displays a list of food items.

**3.** User requests to delete a food item from the list.

**4.** SimplyKitchen deletes the food item from the food inventory and displays a success message.

Use case ends.

**Extensions:**

**2a.** The list is empty.

Use case ends.

**3a.** SimplyKitchen detects an invalid index corresponding to the food item in the list.

 * **3a1.** SimplyKitchen displays an error message and prompts the user to enter a correct index.

 * **3a2.** User requests to delete another index corresponding to the food item in the list.

   Steps **3a1.** - **3a2.** are repeated until the index entered is correct.

   Use case resumes from step **4**.

<br/>

## D.3. UC03: Edit a food item

**Precondition:** The food item to be edited is currently in the food inventory.

**Guarantees:** The food item is edited from the food inventory.

**MSS:**

**1.** User requests to <ins>find a food item (UC05)</ins> or <ins>list all food items (UC06)</ins>.

**2.** SimplyKitchen displays a list of food items.

**3.** User requests to edit a food item from the list.

**4.** SimplyKitchen edits the food item in the food inventory and displays a success message.

Use case ends.

**Extensions:**

**2a.** The list is empty.

Use case ends.

**3a.** SimplyKitchen detects an invalid index corresponding to the food item in the list.

 * **3a1.** SimplyKitchen displays an error message and prompts the user to enter a correct index.

 * **3a2.** User requests to edit another food item in the list.

   Steps **3a1.** - **3a2.** are repeated until the index entered is correct.

   Use case resumes from step **4**.

**3a.** SimplyKitchen detects an error in the user's edited food item.

 * **3a1.** SimplyKitchen displays an error message and prompts the user to enter a correct edited food item.

 * **3a2.** User enters another edited food item.

   Steps **3a1.** - **3a2.** are repeated until the edited food item entered is correct.

   Use case resumes from step **4**.

<br/>

## D.4. UC04: Change the quantity of a food item

**Guarantees:**  The food item has its quantity changed.

**MSS:**

**1.** User requests to <ins>find a food item (UC05)</ins> or <ins>list all food items (UC06)</ins>.

**2.** SimplyKitchen displays a list of food items.

**3.** User requests to change the quantity of a food item.

**4.** SimplyKitchen changes the quantity of the food item in the food inventory and displays a success message.

Use case ends.

**Extensions:**

**2a.** The list is empty.

Use case ends.

**3a.** SimplyKitchen detects an invalid index corresponding to the food item in the list.

 * **3a1.** SimplyKitchen displays an error message and prompts the user to enter a correct index.

 * **3a2.** User requests to change the quantity of another food item in the list.

   Steps **3a1.** - **3a2.** are repeated until the index entered is correct.

   Use case resumes from step **4**.

**3a.** SimplyKitchen detects an error in the user's input quantity.

 * **3a1.** SimplyKitchen displays an error message and prompts the user to enter a correct input quantity.

 * **3a2.** User enters another input quantity.

   Steps **3a1.** - **3a2.** are repeated until the input quantity is correct.

   Use case resumes from step **4**.

<br/>

## D.5. UC05: Find a food item

**Guarantees:**  All food items in the food inventory that match the query are listed.

**MSS:**

**1.** User requests to list food items according to the description, priority, expiry date and/or tag.

**2.** SimplyKitchen displays all food items matching the search query.

Use case ends.

**Extensions:**

**1a.** SimplyKitchen detects an error in the search query.

 * **1a1.** SimplyKitchen displays an error message and prompts the user to enter a correct search query.

 * **1a2.** User enters a new search query.

   Steps **1a1.** - **1a2.** are repeated until the search query entered is correct.

   Use case resumes from step **2**.

<br/>

## D.6. UC06: List all food items

**Guarantees:**  All food items in the food inventory are listed.

**MSS:**

**1.** User requests to list all food items in the food inventory.

**2.** SimplyKitchen displays all food items in the food inventory.

Use case ends.

<br/>

## D.7. UC07: Clear all food items

**Guarantees:**  All food items in the food inventory are cleared.

**MSS:**

**1.** User requests to clear all food items in the food inventory.

**2.** SimplyKitchen removes all food items in the food inventory and displays a success message.

Use case ends.

<br/>

## D.8. UC08: Sort food items by expiry date

**Guarantees:** The food items in the food list are sorted by expiry date.

**MSS:**

**1.** User requests to sort the food list by expiry date.

**2.** SimplyKitchen sorts the food list by expiry date.

Use case ends.

**Extensions:**

**2a.** The list is empty.

Use case ends.

<br/>

## D.9. UC09: Sort food items by priority

**Guarantees:** The food items in the food list are sorted by priority.

**MSS:**

**1.** User requests to sort the food list by priority.

**2.** SimplyKitchen sorts the food list by priority.

Use case ends.

**Extensions:**

**2a.** The list is empty.

Use case ends.

<br/>

## D.10. UC10: Sort food items by description

**Guarantees:** The food items in the food list are sorted by description.

**MSS:**

**1.** User requests to sort the food list by description.

**2.** SimplyKitchen sorts the food list by description.

Use case ends.

**Extensions:**

**2a.** The list is empty.

Use case ends.

<br/>
<div style="page-break-after: always;"></div>

## D.11. UC11: Undo most recent undoable command

**Guarantees** The most recent undoable command (add, changeqty, clear, delete, edit, sortdesc, sortexpiry, sortpriority) requested will be undone.

**MSS:**

**1.** User requests to undo.

**2.** SimplyKitchen displays the food list before the most recent undoable command was requested.

Use case ends.

**Extensions:**

**2a.** No undoable commands were executed.

Use case ends.

<br/>

## D.12. UC12: Redo most recent undo command

**Guarantees** It redoes the most recent undo command.

**MSS:**

**1.** User requests to redo.

**2.** SimplyKitchen displays the food list after the most recent undo command was requested.

Use case ends.

**Extensions:**

**2a.** No undo commands were executed.

Use case ends.

<br/>

[Back to top](#table-of-contents)
<div style="page-break-after: always;"></div>

# Appendix E: Non-Functional requirements

* The app should work on any mainstream OS as long as it has Java 11 or above installed.
* The app should be able to hold up to 1000 food items without a noticeable sluggishness in performance for typical usage.
* A user with above average typing speed for regular English text (i.e. not code, not system admin commands) should be able to accomplish most of the tasks faster using commands than using the mouse.
* A user should be able to see food items clearly on the GUI to facilitate command typing.

[Back to top](#table-of-contents)

--------------------------------------------------------------------------------------------------------------------

# Appendix F: Instructions for manual testing

Given below are instructions to test the app manually.

<div markdown="span" class="alert alert-info">

**:information_source: Note:**<br>

These instructions only provide a starting point for testers to work on; testers are expected to do more *exploratory* testing.

</div>

## F.1. Launch and shutdown

1. Initial launch

   1. Download the jar file and copy into an empty folder

   2. Double-click the jar file Expected: Shows the GUI with a set of sample contacts. The window size may not be optimum.

2. Saving window preferences

   1. Resize the window to an optimum size. Move the window to a different location. Close the window.

   2. Re-launch the app by double-clicking the jar file.<br>
      Expected: The most recent window size and location is retained.

[Back to top](#table-of-contents)

## F.2. Deleting a food item

1. Deleting a food item while all food items are being shown

   1. Prerequisites: List all food items using the `list` command, or use `find` command to display the list of food matching the search fields.
      There should be multiple food items displayed in the food list.

   2. Test case: `delete 1`<br>
      Expected: The first food item is deleted from the food list. Details of the first food item is shown in the result box.

   3. Test case: `delete 0`<br>
      Expected: No food item is deleted. An error message is shown in the result box.

   4. Other incorrect delete commands to try: `delete`, `delete x`, `...` (where x is larger than the list size)<br>
      Expected: Similar to previous.

[Back to top](#table-of-contents)

## F.3. Changing the quantity of a food item

1. Changing the quantity of a food item while some or all food items are being shown

   1. Prerequisites: List all food items using the `list` command, or use `find` command to display the list of food matching the search fields.
   There should be multiple food items displayed in the list.

   2. Assumption: The first food item displayed in the food list has a quantity of 5.00.

   3. Test case: `changeqty 1 a/+1.00`
      Expected: The first food item has its quantity updated to 6.00. Updated details of the first food item is shown in the result box.

   4. Test case: `changeqty 1 a/1.00` or `changeqty 1 a/+1.000`
      Expected: The first food item remains the same. An error message similar to the one shown below is displayed in the result box.
      
      ![Error message](images/ChangeQuantityErrorMessage.png)

   5. Test case: `changeqty 1 a/x` (where x is smaller than or equal to -5.00 OR larger than +99,995.00)
      Expected: The first food item remains the same. An error message similar to the one shown below is displayed in the result box.

      ![Error message](images/ChangeQuantityConstraintErrorMessage.png)

[Back to top](#table-of-contents)

## F.4. Sorting the food list

1. Sorting the food list while some or all food items are being shown

   1. Prerequisites: List all food items using the `list` command, or use `find` command to display the list of food matching the search fields.
   There should be multiple food items displayed in the list. 

   2. Test case: `sortdesc`<br>
      Expected: The food items in the list is sorted by description.

   3. Test case: `sortpriority`<br>
      Expected: The food items in the list is sorted by priority from high to low.

   4. Test case: `sortexpiry`<br>
      Expected: The food items in the list is sorted by expiry date from oldest to newest.

[Back to top](#table-of-contents)

## F.5. Saving data

1. Dealing with missing/corrupted data files

   1. Test case: Delete the `foodInventory.json` file in the `data` folder.<br>
      Expected: Status message shows that the data file has not been found and that the application will be starting with a sample food inventory.
   
   2. Test case: Remove the `description` field from one of the food items in the `foodInventory.json` file in the `data` folder.<br>
      Expected: An error message shown in the status message reporting corrupted data file format. 
      Error message also gives scenarios of how to proceed, either fix the data file or start with a new inventory by adding a food item. 
      
   3. Test case: Remove any of the other fields - `expiryDate`, `priority`, `quantity`, `tagged` - from a food item in the `foodInventory.json` file.<br>
      Expected: Similar to previous.

[Back to top](#table-of-contents)

--------------------------------------------------------------------------------------------------------------------

# Appendix G: Effort

Overall, our team is satisfied to create SimplyKitchen as a product that is both intuitive and user-friendly for our target audience, domestic individuals who manage their food inventory at home.
Throughout this fulfilling journey, our team has cultivated a good project system and has been able to meet the deadlines of our tasks.
Our team has managed to contribute about 12kLOC, roughly the same amount as that of developing AB3.<br>

The `Food` model in SimplyKitchen is more complex as compared to the `Person` model in AB3.
The `Food` model has attributes such as `Expiry Date` and `Quantity` where ensuring validation of the inputs was complex.
For example, the `Quantity` class includes a compulsory value and an optional unit.
Parsing of the quantity input needs to take into account many different constraints such as the size limit, the number of decimal places, the length of the unit and the characters allowed in the unit.
Restricting the inputs to these various conditions was tedious but necessary and helpful to the user.<br>
 
A challenge our group had faced was to be concise with the constraints and functionality of our `add` and `find` commands in the User Guide.
Due to the many parameters of these two commands, our explanations were detailed but quite long.
We had to strike a balance between being concise while ensuring that the users can take full advantage of our commands so that they can have an enriching experience using our application to manage their food inventory.<br>

Another key challenge for our group was to decide on the type of sorting to implement in SimplyKitchen.
To preserve the CLI nature of the application, we decided to introduce three new sorting commands to sort food items based on the expiry date, description and priority.
Sorting by description proved to be difficult as we decided to enhance sorting by lexicographical order to account for uppercase and lowercase characters.
This enables the user to sort the list more intuitively. This way, users would not have items with descriptions differing by the casing of the first characters (e.g. “apple” and “Apple juice”) far apart in the list with a lexicographical order.<br>

We also implemented many new commands such as `changeqty`, `undo`, `redo`, and so on.
These new commands brought about new ways to interact with the application unlike AB3.
For example, the `changeqty` command relieves users of the burden of having to calculate a new quantity of the food item every time he or she buys/uses/discards food items.<br>

In terms of UI, a significant change we made which catered very well to our target audience was the creation of a pop-up window to display the list of expired food items.
This pop-up window can also be called by using the `expired` command.
Additionally, a side panel showing the list of food items that are expiring within a week was added to the main application window.
We have to ensure that this side panel is constantly updated whenever the user adds/edits a food item that expires within a week from the current date, which was slightly challenging.<br>

Each of these challenges was learning experiences for our team members.
As a team, we are glad to have overcome these challenges to create an impressive, immersive and lasting product, SimplyKitchen.<br>

[Back to top](#table-of-contents)

--------------------------------------------------------------------------------------------------------------------
