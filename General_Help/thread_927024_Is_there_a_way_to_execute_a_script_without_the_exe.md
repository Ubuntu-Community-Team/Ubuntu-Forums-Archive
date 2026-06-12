---
title: "Is there a way to execute a script without the executable flag?"
date: 2008-09-22
forum: General Help
---

### Post by Endolith on 2008-09-22
If a script is marked executable, you can execute it with 

```
./scriptname
```

This will read the script, open a new shell according to the script's #! shebang, and then execute the rest of the script inside that shell, if I understand correctly.

You can also use [the source command]("http://learnlinux.tsf.org.za/courses/build/shell-scripting/ch10s02.html"):

```
. scriptname
```

or 

```
source scriptname
```

This will ignore the shebang and not open a new shell, but will run the script's commands in the shell you are currently using.  If the commands are not compatible with your shell, it will screw up.

Is there a way to run a script that doesn't have the executable flag, but have it behave as in the first example ./scriptname?

---

### Post by Titan8990 on 2008-09-22
No, the only way to do this is with example 3 by adding the the shebang to the command.

For example if I made a file called "test" and added "ifconfig" to it w/o a shebang or making it a executable I can execute like so:


sudo sh ./test


This will execute the non-executable because essentially it is executing sh which is an executable.

---

### Post by vanadium on 2008-09-22
No: it is against the safety principles.

---

### Post by xebian on 2008-09-22
> **Titan8990 said:**
> No, the only way to do this is with example 3 by adding the the shebang to the command.

For example if I made a file called "test" and added "ifconfig" to it w/o a shebang or making it a executable I can execute like so:


sudo sh ./test


This will execute the non-executable because essentially it is executing sh which is an executable.

Why bother with the ./ ?

sh script.file is enough.

---

### Post by Endolith on 2008-09-22
> **Titan8990 said:**
> No, the only way to do this is with example 3 by adding the the shebang to the command.

Oh, right.  I figured out I could do that, too; just running the script through the interpreter directly:

```
sh scriptname
```or 

```
python scriptname
```and then the files don't need to be executable. But then you need to know which interpreter the script works in.  Is there a way to interpret the script like this, but divert it into whichever interpreter is specified in the shebang?  Is there a "universal interpreter" that will call the appropriate interpreter from the shebang?  Maybe using env or something?

---

### Post by Titan8990 on 2008-09-22
I would have to say that it would be a security issue if you could do something like this....

---

### Post by Endolith on 2008-09-22
> **Titan8990 said:**
> I would have to say that it would be a security issue if you could do something like this....

Why?  You can execute the script directly using sh or python interpreter.  There's certainly nothing stopping you from writing a program that reads the script as a regular file, parses the shebang, and then sends the script to the appropriate interpreter.  So it's certainly possible to do this.  I'm just wondering if there's a single command that does this automatically.

---

### Post by Titan8990 on 2008-09-22
With the method described it requires human interaction. If there was an automated method I would think that it would be easier for malicous code to be executed on a machine unknowingly to the user.

---

### Post by Endolith on 2008-09-22
> **Titan8990 said:**
> With the method described it requires human interaction.

No.  The method I just described could be done in a script.  It doesn't require any user intervention.  Create an executable Python script that does what I just said, call it "interpret".  Then you could call non-executable scripts with "./interpret scriptname", and it would put scriptname through whichever interpreter is specified in the scriptname shebang.

So it's currently possible, and I don't see any reason for it to be a "security precaution".  I imagine this script doesn't need to be written, though; there's probably already a single command like env/exec/source that does this automatically.

---

