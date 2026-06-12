---
title: "terminal redirect question."
date: 2008-09-19
forum: General Help
---

### Post by sygard on 2008-09-19
Hi!

I'm trying to redirect some input and output from a program to a file.
I have tried this:

bash# java Program < infile > outfile.txt


"Program" takes commands sent from infile - line by line, processes data and prints some output.

"infile" contains commands which in normal operation is typed in from the keyboard to the program, but as I'm trying to automate this process - for testing purposes, I store the commands in this file so I don't have to manually input them each time I run the program.

"outfile.txt" should contain all information sent to and from the program "Program".


This seems to work fine, but outfile.txt will not contain the commands sent from infile, eg. the commands will not show up in the file outfile.txt.

Is there any way to make this happen ?

I have also tried redirecting both stdout and stderr to outfile.txt using this command: 

java Program < infile &> outfile.txt


Thanks!

---

