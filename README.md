# Yara-project

# Project Report: Introduction to Yara Rules

## Introduction to Yara Rules

Yara is an open-source tool primarily used for identifying and classifying malware. It allows security researchers and analysts to create rules that describe patterns or characteristics of malicious files. These rules can then be used to scan and match files, processes, or other data for specific traits indicative of malware or suspicious activities.

## My First Yara Rule

The proprietary language that Yara uses for rules is fairly trivial to pick up, but hard to master. This is because a rule is only as effective as your understanding of the patterns you want to search for.

Using a Yara rule is simple. Every Yara command requires two arguments to be valid:
1. The rule file we create.
2. Name of the file, directory, or process ID to use the rule for.

Every rule must have a name and condition.

For example, if I wanted to use "myrule.yar" on directory "somedirectory", I would use the following command:
```
yara myrule.yar somedirectory
```
Note that `.yar` is the standard file extension for all Yara rules. I made one of the most basic rules below.

### Steps to Create My First Yara Rule

1. **Made a file named "somefile"**:
    ```bash
    touch somefile
    ```

2. **Created a new file and named it "myfirstrule.yar"**:
    ```bash
    touch myfirstrule.yar
    ```

3. **Opened "myfirstrule.yar" using a text editor such as nano, input the snippet below, and saved the file**:
    ```bash
    nano myfirstrule.yar
    ```
    Then, entered the following content:
    ```yara
    rule examplerule {
        condition: true
    }
    ```

### Explanation of the Rule

The name of the rule in this snippet is `examplerule`, where I have one condition - in this case, the condition is `condition: true`. As previously discussed, every rule requires both a name and a condition to be valid. This rule has satisfied those two requirements.

Simply, the rule I made checks to see if the file/directory/PID that I specify exists via `condition: true`. If the file does exist, I am given the output of `examplerule`.

### Testing the Rule

To test the rule on the file "somefile" that I made in step one:
```bash
yara myfirstrule.yar somefile
```
If "somefile" exists, Yara will say `examplerule` because the pattern has been met - as seen below:

### Verifying the Rule
```bash
yara myfirstrule.yar somefile 
examplerule somefile
```
If the file does not exist, Yara will output an error such as the one below:

### Error Output When the File Does Not Exist
```bash
yara myfirstrule.yar sometextfile
error scanning sometextfile: could not open file
```

Congratulations! I have successfully created and tested my first Yara rule.
