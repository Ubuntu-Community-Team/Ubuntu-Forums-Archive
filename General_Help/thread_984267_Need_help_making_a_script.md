---
title: "Need help making a script"
date: 2008-11-16
forum: General Help
---

### Post by ibs on 2008-11-16
I want to make a script that extracts a file from multiple rar archives and then automatically deletes the archives. 

For example, i have File.part1.rar, File.part2.rar and File.part3.rar and i do:

rar x File.part1.rar to extract the file from the archives. And then i do:

rm File.part*.rar to delete the archives.

Could someone help me make a script like that?

---

### Post by Keith Hedger on 2008-11-16
You could try somthing like this:```
#!/bin/bash

for arg in $@
	do
		echo $arg
		rar x "arg"
		rm "$arg"
	done
```
Save this as (for instance) extractfiles and dont forget to set the executable bit.
And call it from the command line like this:```
./extractfiles File.part1.rar File.part2.rar File.part3.rar
```
Also check out the Advanced Bash Scrcripting Guide in the repos

---

### Post by ibs on 2008-11-18
The script didn't work with "arg" behind rar x so i tried to change it to $arg like this:

----
#!/bin/bash

for arg in $@
	do
		echo $arg
		rar x $arg
		rm "$arg"
	done

--

Now the script works when handling just one rar archive. But when i try it on multiple archives, the script only deletes part1, or the first archive part.

---

### Post by Keith Hedger on 2008-11-19
my mistake i forgot the '$' cant see why it is only operating on one file try posting the output from the script, i dont have rar installed but i am getting the correct errors and file names outputed are the rar files in the same dir as the script? if not u probably need to use a full/relative path.

---

