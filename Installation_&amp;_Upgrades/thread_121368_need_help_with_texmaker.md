---
title: "need help with texmaker"
date: 2006-01-25
forum: Installation &amp; Upgrades
---

### Post by adamkat on 2006-01-25
I backported the latest taxmaker but am not able to set the paths of each indevidual program.
I am a linux beginner so please explain in detail.
Thanks

---

### Post by adamkat on 2006-01-29
Sorry, I mean texmaker not taxmaker.
Any ways, I am using tetex3 but I still don't understand how to set the path, please help me step by step, as I said, I'm a total newbie.
Thanks

---

### Post by neoflight on 2006-02-14
Exactly. same problem here...and more...
I had  posted the same message [here]("http://www.ubuntuforums.org/showthread.php?t=129010&page=2")

I hope this is the best place for the post....SO....

I have installed everything from texmaker to texlive succesfully. I can run latex commands (almost all; latex, dvips....etc all of them) from the command line or using gedit os anyother editor for that matter EXCEPT texmaker!!!

I have set up the commands from the texmaker config menu. But all i am getting is "log file not found" ... when i run the same tex file from the shell using latex command it creates all the files needed without any latex errors. i mean i have .log, .dvi, etc in the same folder.

I tried different ways of putting the commands in the texmaker configuration as shown in its own help such as putting the entire latex path in the command. eg

/usr/local/texlive/2005/bin/i386-linux/latex %.tex
[error...a message comes saying "process started" in the bottom message window...then it changes to "Error : could not start the command"]
and
/usr/local/texlive/2005/bin/i386-linux/latex -interaction=nonstopmode %.tex
[same error as above..]
and
latex -interaction=nonstopmode %.tex [error- "log file not found"]
and simply
latex %.tex
[error "log file not found"]

note: once i have the log file in the folder from a command line latex run texmaker runs...but none of the other commands work (the command icons)...but why is texmaker not making log file? why is anyother commands not working?

whats happening here? i have all the PATH variables set etc..
any help would be appreciated...thanks

---

### Post by neoflight on 2006-02-17
[QUOTE=adamkat]I backported the latest taxmaker but am not able to set the paths of each indevidual program.
I am a linux beginner so please explain in detail.
Thanks[/QUOTE]

Here is a [howto]("http://http://www.ubuntuforums.org/showthread.php?t=131507&highlight=texlive") on texlive+texmaker
let me know if it works for you or not.

---

