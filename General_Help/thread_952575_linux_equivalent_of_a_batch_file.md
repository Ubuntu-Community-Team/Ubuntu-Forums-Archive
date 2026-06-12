---
title: "linux equivalent of a batch file"
date: 2008-10-19
forum: General Help
---

### Post by aaronmarsh632 on 2008-10-19
Hi, you know in windows you can create a batch file with commands which are run when the batch file is executed, what is the linux equivalent?

Thanks

---

### Post by northern lights on 2008-10-19
The *nix equivalent would be a shell script. Ubuntu's default shell is bash.

[BASH Programming Introduction]("http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html") might prove a worthy read.

---

### Post by mike2357 on 2008-10-19
Linux has a very rich command line language, and commands can be put in a file and executed, like a .bat file in Windows.  To start, you create a plain text file and put your commands in it.  You then make your file executable.

For instance, if your file name is "my_file", execute this command to make it executable:

chmod 755 my_file

To run it, execute this command:
./my_file

If you are just getting started with Linux commands, enter "linux command line introduction" in your favorite search engine.

---

### Post by aaronmarsh632 on 2008-10-19
This is great, and Thanks for the quick reply

---

### Post by vanadium on 2008-10-19
The shell script.

Equally as in Windows a text file containing commands.

Usually, you will find an extra first line, similar to #!/bin/bash. This line instructs which command processor should execute the commands. You do not have such choice in Windows.

Running such a batch file or script involves typing the name of the file similar to Windows. However, if the file is in your current directory, you need to precede the name with ./, e.g.

./myscript

Before you can execute a script in linux, you first must declare it "executable". This is because linux is designed to be safe. It won't try to run any file like Windows does. You can make it executable using the file manager or with the command chmod

chmod +x myscript

will mark the file as "executable" . After that, you can run the file with

./myscript

If the file is in another directory that is in your search path, you can execute it simply by typing its name.

---

