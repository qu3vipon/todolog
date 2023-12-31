# todolog
Comment is not enough. Actively Manage ToDos!

## Features
- If there is any ToDo that is past due, logs a message.
- Different log levels can be applied for each ToDo.
- ToDo can be actively managed as a separate TOML file, not as a comment.
- Logging can be turned off.
- Each module can have a separate TOML file. 
- Configurations in TOML file is cached on memory without continuing to read.

## Usage
1. Install todolog
   ```shell
   pip install todolog
   ```

2. Specify the name of the configuration file to be used for todo logging in `pyproject.toml`.
   - `pyproject.toml` must be under the source root.
   ```toml
   # pyproject.toml
   [tool.todolog]
   filename = "todolog.toml"
   default_log_message = "This is a default log message."
   ```

3. Write a configuration for ToDos in TOML format.
   ```toml
   # todolog.toml
   [key1]
   responsible = "qu3vipon@gmail.com"
   message = "[ToDo] This is a log message."
   due = 2023-12-31
   log_level = "WARNING"
   description = """
   This is a description about a ToDo.
   It can be written very long, but it is ignored at run time.
   """
   ```

4. Add a decorator to the function that should be managed.
   ```python
   @todo(key="key1")
   def deprecated_function():
      pass
   ```

5. (Optional) Logging can be turned off.
   ```python
   @todo(key="key1", ignore=True)
   def deprecated_function():
      pass
   ```
