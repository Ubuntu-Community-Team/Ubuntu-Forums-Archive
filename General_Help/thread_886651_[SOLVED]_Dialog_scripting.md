---
title: "[SOLVED] Dialog scripting"
date: 2008-08-11
forum: General Help
---

### Post by WallyWest on 2008-08-11
Hello,
I am trying to learn some basic shell scripting and would like to convert a script I have that runs some telnet commands I use all the time from its original MORT script into bash. Its become obvious that some dialog boxes should be created to select one of multiple IP's to pass into the telnet session, and once there in session, have another box that contains the commands. I am asking for any documentation or advice on having user input from the dialog box read as a command in the shell.
THanks.

---

### Post by kaibob on 2008-08-11
> **WallyWest said:**
> ...I am asking for any documentation or advice on having user input from the dialog box read as a command in the shell.
THanks.

Deleted by Kaibob--not sure about question

---

### Post by WallyWest on 2008-08-11
I have looked at those alternative options such as zenity but I don't know how to compile and I've only found versions that require that. I felt like it would be easier to get through the struggles of regular old dialog package than learning to compile and use an alternate to it. I really don't have much knowledge though and only rely on my ability to understand documentation I can find. (Whether thats a man page or a tutorial) So if more experienced people think I should try zenity or anything else I will try that.
THanks.

---

### Post by kaibob on 2008-08-11
> **WallyWest said:**
> I have looked at those alternative options such as zenity but I don't know how to compile and I've only found versions that require that.

I may be in old-and-confused mode this morning, but zenity is in the repo's. No compiling is required. 

The following pages contain some examples:

[http://linux.byexamples.com/archives/259/a-complete-zenity-dialog-examples-1/](http://linux.byexamples.com/archives/259/a-complete-zenity-dialog-examples-1/)

[http://linux.byexamples.com/archives/265/a-complete-zenity-dialog-examples-2/](http://linux.byexamples.com/archives/265/a-complete-zenity-dialog-examples-2/)

I get the feeling that I don't understand what you're asking--perhaps others can be of more help.

---

### Post by WallyWest on 2008-08-11
> **kaibob said:**
> I may be in old-and-confused mode this morning, but zenity is in the repo's. No compiling is required. 

The following pages contain some examples:

[http://linux.byexamples.com/archives/259/a-complete-zenity-dialog-examples-1/](http://linux.byexamples.com/archives/259/a-complete-zenity-dialog-examples-1/)

[http://linux.byexamples.com/archives/265/a-complete-zenity-dialog-examples-2/](http://linux.byexamples.com/archives/265/a-complete-zenity-dialog-examples-2/)

I get the feeling that I don't understand what you're asking--perhaps others can be of more help.
I probably should have thought of that earlier.... Seems you can be young and confused too haha. (Or is that called ignorance?) ill post back if I encounter more roadlblocks...( like those errors between the keyboard and chair that seem omnipresent)
THanks,

---

### Post by WallyWest on 2008-08-11
Also, Let me try and better explain my problem.
I am required to modify several private IP's daily. I do this through Telnetting into a switch and using the switch's specific commands to make the necessary changes. I would like to create a script that allows me to pick the IP that needs configured from a dialog box of some sort and have it start a telnet session with that IP. Then once inside the telnet session I would like another dialog box to display some commonly used commands and allow me to just select the command and have it run. There's a little more to it but that is the meat of the script and should be addressed first. I hope that makes more sense.
THanks

---

### Post by bodhi.zazen on 2008-08-11
I do not see why zenity will not do all this and more ...

[http://linux.byexamples.com/archives/259/a-complete-zenity-dialog-examples-1/](http://linux.byexamples.com/archives/259/a-complete-zenity-dialog-examples-1/)

    [http://linux.byexamples.com/archives/265/a-complete-zenity-dialog-examples-2/](http://linux.byexamples.com/archives/265/a-complete-zenity-dialog-examples-2/)

---

### Post by WallyWest on 2008-08-11
zenity *is* working just fine. thanks guys... 
THanks.

---

