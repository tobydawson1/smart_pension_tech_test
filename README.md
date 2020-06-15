# Customer Service Support Technician Tech Test
Test for CS Support candidates

## Requirements

Allowing for setting up the project, this tech test should take around 2 hours to complete.

1. Find the cause of issues in the application:
* There are three bugs to find
* You are not required to *fix* the bugs, your aim is to __identify__ what is causing them

2. Document your process:
  * What did you notice/find?
  * What are your recommendations?

## Getting Started
These instructions will get the application up and running on your local machine for bug finding purposes.

* Install Ruby [Ways of Installing Ruby](https://www.ruby-lang.org/en/downloads)
* Install Yarn [Ways of Installing Yarn](https://yarnpkg.com/lang/en/docs/install)
* Clone this git repository `git clone git@github.com:smartpension/smart-cs-support-test.git`
* cd into the locally cloned repo `smart-cs-support-test`
* Run `bin/setup` 
* Start up your web-server (see the output of `bin/setup`)
 * If you get an error with: `getaddrinfo: nodename nor servname provided, or not known (SocketError)` 
   * Try running your server with`./bin/rails server -b 0.0.0.0`
     
* Navigate to: http://localhost:3000

Remember to document __how__ you identified the bugs and attach your findings to your email back to us, have fun!

## Bugs and solutions 

### Bug 1 

```
Error says that the surname form is blank when you try to add a new employee even if the labelled surname form is filled in. This is due to ‘new.htmp.erb’ the second form is labeled as surname but the input it accepts is stored as the middle name so the surname in the database is therefore blank causing the error
```

### Possible fix

```
A fix for this could be done a number of ways. I can see that a separate migration has been added   called ‘add_middle_name_to_employees_table’ what this tells me is that middle name is a required piece of information so simply changing the form asking for the middle name to the surname may not suffice. Adding another form correctly assigned to take the take data for the middle name is a good option and changing the now 3rd form to correctly input data into the surname row would work. 
```
### Bug 2

```
When you try to edit a pre existing employee it throws up an error regarding ID’s. This is due to the edit_company_employee_path being wrong. I figured this out by playing with the href.
```
### Possible fix

```
A fix would be to alter line 11 in ‘show.html.erb’ the link to edit should have (@company, @employee) within its parenthesis. This will give the ID’s in the correct order. 
```

### Bug 3

```
When clicking ‘show’ in order to check the employees for various company’s, it is always taking you to the first company in the database. 
```

### Possible fix

```
My fix for this would be to look into ‘companies_controller’ and look for the ‘show’ method and specifically line 11. @company = Company.first is utilising a method that will always show the the first piece of data in the database. Simply removing this line should solve this bug. 
```