## TEST PLAN

**1 Introduction**

```
The Test Plan has been created to communicate the test approach to team members. This
document will clearly identify what the test deliverables will be and what is deemed in and
out of scope.
```

1.1 Objectives

```
The parse_actions function is utils.py is used to correctly parse the data passed in and return the correct dataframe object.
This test plan is to test the function of parse_action  with different ticker data and possibly found any bugs inside.
```

1.2 Team Members

```
* Shiyu Xiu - Unit Testing the parse_actions for dividend case
* Luke Kim - Unit Testing the parse_actions for split case
* Ruochen Lin - Unit Testing the parse_actions for date & time match correct and empty input

```

**2 Problem found in Research phase**

```
date & time error when date input is before the date of electronic stock market was created
```

**3 Risks**

The following risks have been identified and the appropriate action identified to mitigate
their impact on the project. The impact (or severity) of the risk is based on how the project
would be affected if the risk was triggered. The trigger is what milestone or event would
cause the risk to become an issue to be dealt with.

1.The change of the structure of parameter data and the test case we had will be invalid:

```
Risk: Medium
Trigger: structure of parameter data is changed
Mitigation Plan: Update the test case when the trigger happened
```

2.Changes to the parse_action function may negate the tests already written and we may lose test cases already written:

```
Risk: High
Trigger: Loss of all test cases
Mitigation Plan: Export data prior to any upgrade, massage as necessary and re-import after upgrade.
```

3.Stock mock data might be inaccurate:

```
Risk: Low
Trigger: Retrieving data through run.py contains outdated/wrong data
Mitigation Plan: Check the yahoo stock website to validate the data
```

4.Changes to the date under dividends may lead to inaccurate display of date and time:

```
Risk: Low
Trigger: if the date of input is inaccurate.
Mitigation Plan: Correct time by adding get current dataTime function to compare.
```

**4 Test Approach**

4.1 Planned tests:

```

1.test when data has no dividends and splits:

```

- test if the returned dataframe is empty dataframe

```

2.test when data has only dividends:

```

- test if the returned dataframe is None
- test if the returned dividend dataframe is empty
- test if the returned splits dataframe is empty
- test if the dataframe returned matches with expected dataframe
- test if the date and time dataframe returned matches expected dataframe
- test if the empty data and time dataframe reuturned matched expected dataframe

```

3.test when data has only splits:

```

- test if the returned dataframe is None
- test if the returned dataframe contains splits
- test if the returned dataframe does not contain dividends
- test if the returned dataseries matches the expected output listed
- test if the date and timne dataframe returned matches expected dataframe
- test if the empty data and time dataframe reuturned matched expected dataframe

```
4.test when the date passed in is invalid
```

- test if the returned dataframe has the correct date replacing the invalid date

  4.2 Test approach:

- Create mock data objects as a parameter
- Get the expected correct dataframe objects for later comparison
- Use python unittest library and pass the mock data in the utils.parse_actions
- Compare the result.

**5 Test Environment**

```

MacOs Big Sur 11.2.
Windows 10 Home 64-bit
Python 3.9.2 64 bit version

```
