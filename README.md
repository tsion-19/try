[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-24ddc0f5d75046c5622901739e7c5dd533143b0c8e959d652212380cedb1ea36.svg)](https://classroom.github.com/a/gsWy35qJ)
# Exercise 1
Consider the Python application in the `exercise_1` folder. Write a GitHub Actions' workflow to implement a CI/CD Pipeline which performs the following:

1. Runs the `pycodestyle`, a Python linter, to check that all Python files within `exercise_1` are PEP8 (a Python style-guide) compliant.

2. Runs the `setup.py` script, by running `python3 -m build` to package the application. This creates a `*.whl` file in a `dist` folder, which can be installed by `pip install file.whl`.

3. Runs the tests modules `tests/test_slow_1.py`, `tests/test_slow_2.py`, and `tests/test_fast.py`. If possible, arrange the jobs in such a way that `test_fast.py` is run first, and `test_slow_*.py` are executed later, in parallel.

4. Finally, execute the `deploy.sh` script.

# Exercise 2
The Conventional Commits specification is a lightweight convention on top of commit messages. It provides an easy set of rules for creating an explicit commit history; which makes it easier to write automated tools on top of.

A simplified Conventional Commits-like commit message could be structured as follows:

```
<type>: <short description>

<tags>

<detailed description>
```

where: `<type>` is one of `FIX`, `FEATURE`, `BREAKING CHANGE`, `<short description>` is a string which shortly describes the contents of the commit (less than 140 characters) and `<detailed description>` is a description without space constraints. A `tag` is a string with no whitespaces that starts with `@` (e.g., `@something`), and `<tags>` is a space-separated list of tags.

Write a `commit-msg` Git hook that rejects commits whose commit message does not conform to the above specification. All parts are mandatory.

# Exercise 3
Your task is to create a simple password validator library, which implements the following features:

- Expose an API to let developers define custom validation criteria, such as:
	- Passwords' minimum, maximum length; 
	- Set of allowed/forbidden characters, words;
	- ...
- Expose an API that lets developers _compose_ available, previously defined validation criteria;

Write a CLI interface to test a password. Something like:
```bash
validate correct-horse-battery-staple criteria.json
``` 

where `correct-horse-battery-staple` is a candidate password and`criteria.json` is a file which stores a sequence of validation criteria. 

You are free to use whatever file format and serialization schema to encode/decode validation criteria into a file, `json` is only an example. Develop your application using TDD principles. Please annotate in a `tdd_requirements.txt` any additional requirements you deem important as you discover them, and refer them to the tests you implement.

# Exercise 4
Your friends are developing a microservice to check the status of the Ponte Coperto Coffee Machine. Issuing a GET to its endpoint, you get a JSON response which is as follows:

```javascript
{
  "status": {
    "functioning": true,	// Currently works?
    "last_refill": 8		// Days since last refill
  },
  "queue": {
    "queue_length": 12,		// People currently in queue
    "estimate_ttc": 320		// Estimated time-to-coffee, seconds
  }
}
```

Your task is to write a function `good_pause` which implements the following logic:

1. Returns `False` if the coffee machine is not functioning or if its `last_refill` is more than a week ago; 
2. Returns `False` if there are more than 5 people in queue or if the `estimate_ttc` (time-to-coffee) is greater than 5 minutes.

In all other cases, it should return `True`. If you are using Python, you can check out the `requests` library for HTTP.
