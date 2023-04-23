#  daml version
SDK versions:
  2.6.1  (project SDK version from daml.yaml)
  2.6.3  (latest release, not installed)

java -version
openjdk version "11" 2018-09-25

echo $JAVA_HOME

# Case1.daml

In this example, we define a Case template that represents a case with an owner, title, description, status, manager, and employee. We also define the Role and CaseStatus data types to represent the participant roles and case statuses.

The Case template has four choices: CreateCase, AssignManager, AssignEmployee, and CloseCase. The CreateCase choice is used by the owner to create a new case with a title, description, manager, and employee. The AssignManager choice is used by the current manager to assign a new manager to the case. The AssignEmployee choice is used by the current manager to assign a new employee to the case. The CloseCase choice is used by the employee to close the case.

Each choice has a controller that specifies which party is allowed to exercise the choice, and a do block that specifies the actions that should be taken when the choice is exercised. For example, the AssignManager choice archives the current case and creates a new case with the same owner, title, and description, but with a new manager and the status set to InProgress.

This smart contract can be used to manage simple cases in a decentralized and secure way.

# Case2.daml

In this example, we define a Case template that represents a case with an owner, title, description, status, manager, employee, and a list of organizations that are allowed to access the case. We also define the Role and CaseStatus data types to represent the participant roles and case statuses.

The Case template has four choices: CreateCase, AssignManager, AssignEmployee, and CloseCase. The CreateCase choice is used by a party from an organization to create a new case with a title, description, manager, and employee. The organizations field of the new case is initialized with a list containing only the party from the organization that created the case.

The AssignManager and AssignEmployee choices are used by the current manager to assign a new manager or employee to the case. The CloseCase choice is used by the employee to close the case.

Each choice has a controller that specifies which party is allowed to exercise the choice, and a do block that specifies the actions that should be taken when the choice is exercised. For example, the CreateCase choice initializes the organizations field of the new case with a list containing only the party from the organization that created the case.

This smart contract can be used to manage cases in a decentralized and secure way across multiple organizations. The organizations field of each case ensures that only parties from the allowed organizations can access the case.

