---
title: "Application launcher doesn't launch"
date: 2008-08-21
forum: General Help
---

### Post by ranbo on 2008-08-21
I have a custom application launcher in my menu bar that I use to launch IntelliJ.  It used to work, but now it doesn't.  If I take the "command" (i.e., "/home/wilsonr/bin/intellij.sh") and type it from the command line, it works, but when I click on the launcher icon, nothing happens.

Any ideas what could be wrong?

---

### Post by iaculallad on 2008-08-21
> **ranbo said:**
> I have a custom application launcher in my menu bar that I use to launch IntelliJ.  It used to work, but now it doesn't.  If I take the "command" (i.e., "/home/wilsonr/bin/intellij.sh") and type it from the command line, it works, but when I click on the launcher icon, nothing happens.

Any ideas what could be wrong?

Since it's a ".sh" file, you should select launcher "Type" as "Application in Terminal" and not just "Application".

-Launcher Setting-

> Type = Application in Terminal

---

### Post by sam1948 on 2008-08-21
try look in: "right click" on the launcher -> properties -> command 
see if there are any special flags 
one option is to remove them and leave the command as u type it in the shell
the other option is to copy that and run it in the shell and see what message u'r getting in return

---

### Post by ranbo on 2008-08-21
Thanks for the quick feedback.

I tried changing it to "Application in Terminal", and still nothing.

When I copy the command verbatim from the launcher properties (/home/wilsonr/bin/intellij.sh) and run it from the command line, it works, so there are no error messages.

---

### Post by ranbo on 2008-08-28
I found that if I output some of the dependent environment variables in the command ("$JDK_HOME") to a file, that I get a different answer from clicking on the icon than I do when I run it from the command line.  Apparently the environment variables are set differently for the toolbar.  Where is it getting those settings?

---

### Post by atroutt on 2009-02-23
I am in the same position. I have tried everything: I tried making the command "/bin/sh /opt/idea-9732/bin/idea.sh" and then I tried "sh /opt/idea-9732/bin/idea.sh" and "/opt/idea-9732/bin/idea.sh" I tried making the launcher type "Application" and "Application in Terminal" and nothing works. It won't launch from a launcher.

If I type "sh /opt/idea-9732/bin/idea.sh" into the terminal the app starts up like perfectly. I do not want to have to open a terminal every morning just to start this app. 

Any other tips out there?

---

### Post by sam1948 on 2009-02-23
did that luncher ever worked ?
is it possible u created it as an root ? (lunching an application from the X server is with user permissions !!)
try creating a new luncher on the desktop and if it works drag it to the panel (on the desktop right click ==> create new luncher).

---

### Post by ranbo on 2009-02-23
I now have my IntelliJ launcher working.  I created a little script in my ~/bin directory called "intellij.sh" that looks like this:

#!/bin/bash
. /home/wilsonr/.bashrc
/usr/local/idea/bin/idea.sh

and then I have my launcher set to run

  nohup /home/wilsonr/bin/intellij.sh > /home/wilsonr/errors.txt &

While I was still getting this working, the "errors.txt" file was ending up getting some errors indicating that IntelliJ didn't know where my java home and other needed variables were being set.  So by sourcing my .bashrc first, I'm able to get this to work.

Surely there's a more elegant solution out there, though, in which the environment run by the panel can have the right paths already available to it, but the best I could do was this workaround.

---

