---
title: "Evolution mail client and Fortune cookies (Signature Tags)"
date: 2008-08-16
forum: General Help
---

### Post by momist on 2008-08-16
I have just been setting up my own 'Fortune' file, and thought the process may be of interest to others.  For those new to the idea, this is a list of 'sayings' otherwise known as fortune cookies or signature tags, randomly selected to add on to your signature.

Ubuntu comes prepared with the 'fortune' software and some tag files, and guidance can be accessed here:
[https://answers.launchpad.net/ubuntu/+source/evolution/+question/42003](https://answers.launchpad.net/ubuntu/+source/evolution/+question/42003)


Here is the process necessary for utilising your own 'fortune' file.

The fortune files available to the /usr/games/fortune program are stored in /usr/share/games/fortunes. There are several in there, which can remain.

Place your own file in the same directory. The file must be composed of the text sequences you require, separated into blocks with the % symbol, and hard 'carriage returns' from your text editor. Have a quick look at /usr/share/games/fortunes/fortunes for the layout. For some reason, my file imported from a windows machine had some other encoding for the line ends, and had to have all the blocks re-defined.  If you hit this problem, the strfile command shows a single string!

Then run the strfile command in a terminal as follows:
user@computer:~$ sudo strfile -r -c% /usr/share/games/fortunes/filename

This will create a filename.dat file in the same place. -r randomises the order, -c% confirms the % sign as the block delimiter (probably not necessary, as it is supposed to be the default).

Now a simple script stored somewhere (home/scripts?) is called from Evolution. Here is the script I'm using:

----
#!/bin/bash

echo "<div>-- </div>"

echo "<p>Ian</p>"

echo "<pre>"
fortune peakoil
echo "</pre>"
----

Remember to use the same name for the script in both places, and the script file must be set to be 'executable' (right click the filename.str and set permissions).

As you can see, peakoil is the name of the file I wish fortune to use.

HTH someone.

Ian

---

