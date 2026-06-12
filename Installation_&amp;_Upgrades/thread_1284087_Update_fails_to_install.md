---
title: "Update fails to install"
date: 2009-10-06
forum: Installation &amp; Upgrades
---

### Post by MarvinZurcher on 2009-10-06
On Oct 2 I did a update. When it installed the update it got to openoffice.org emailmerge and quit. I waited a few minutes and quit the update and now update will not work. I get this message when I try to run update.[ATTACH]130972[/ATTACH] Any help will be appreciated.

---

### Post by wojox on 2009-10-06
You could also try:

```
sudo apt-get -f install
```

---

### Post by MarvinZurcher on 2009-10-06
I did that and it does the same thing. When it gets to adding extension it quits.

---

### Post by ajgreeny on 2009-10-06
Perhaps worth trying synaptic > Edit > Fix Broken Packages, just in case that helps.

---

### Post by MarvinZurcher on 2009-10-06
I can't run synaptic. It says it is already running.

---

### Post by ajgreeny on 2009-10-06
Try ```
killall synaptic
``` in terminal to see if it really is, or look in System > Administration > System Monitor and stop anything related to updating or installing applications, then try synaptic again.

You can only have one front end to apt running at any one time.

---

### Post by MarvinZurcher on 2009-10-06
I ran killall synaptic and it said no process killed.

---

### Post by ajgreeny on 2009-10-06
What about update-manager?

---

### Post by MarvinZurcher on 2009-10-06
Update Manager will not work either.[ATTACH]130995[/ATTACH]

---

### Post by ajgreeny on 2009-10-06
No, what I meant was "is update manager running already?"  Look again in system monitor to see if anything appears to be running that might be associated with installing or updating packages, ie anything with dpkg, apt, synaptic etc etc.

---

### Post by MarvinZurcher on 2009-10-06
I couldn't find anything like that in the system manager.

---

### Post by MarvinZurcher on 2009-10-06
This is what's in my system manager.[ATTACH]131053[/ATTACH][ATTACH]131054[/ATTACH]

---

### Post by hantechbl on 2009-10-06
Can you manually install it?

---

### Post by MarvinZurcher on 2009-10-06
No

---

### Post by hantechbl on 2009-10-06
You have a duplicate of update manager runing terminate that and see if it works if it doesn't then try reinstalling update manager.

---

### Post by MarvinZurcher on 2009-10-07
It's not a duplicate. I had to send two screenshots to get the entire list of operations.

---

### Post by Cheezespread on 2009-10-07
As hantechbl mentioned , there are two entries for "update-manager" . And that is in the same screenshot( 2nd one )

---

### Post by MarvinZurcher on 2009-10-07
I rebooted an it only shows one.[ATTACH]131094[/ATTACH]

---

### Post by ajgreeny on 2009-10-07
Is there a window button for update manager showing in one of your panels, usually the bottom one?  Since 9.04, update manager opens in a minimised window in the background, rather than just the icon showing in the notification area of the panel, and this has stopped quite a few people from using synaptic or Add/Remove when they want to, because update manager is already running.  You can stop this action and go back to the icon appearance, as used to happen, by opening **gconf-editor->Apps->Update-notifier** and remove the check mark from Auto launch.

If the window button is showing, click on it to open the update-manager window and try updating, if not go again to system monitor, scroll down to see if update-manager is running, and if so stop it.  What happens if you try to start update-manager from the menu?

What you have in your new screenshot is update-notifier, quite different from update-manager, and that is OK to have running, but see my info above about changing the notification if you want to.

---

### Post by MarvinZurcher on 2009-10-07
I turned off update notifier. Still have same problem.

---

