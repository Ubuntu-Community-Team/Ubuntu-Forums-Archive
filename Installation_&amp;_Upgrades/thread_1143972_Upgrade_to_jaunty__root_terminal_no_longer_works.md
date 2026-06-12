---
title: "Upgrade to jaunty:  root terminal no longer works"
date: 2009-04-30
forum: Installation &amp; Upgrades
---

### Post by danebramaged on 2009-04-30
Upgraded from 8.1 to 9.04.  Click applications, system tools, root terminal.  Type in password for root terminal.  Jaunty fails to start root terminal.  

sudo works with a regular terminal.

What gives?

---

### Post by Snowhog on 2009-05-03
I have the same issue. Hey guys, how about an answer? Root Terminal is a selectable Item under System Tools. It should then, when selected, work. But it does not. One is prompted for the users password, but no terminal starts up.

---

### Post by overdrank on 2009-05-03
Hi and from [RootSudo]("https://help.ubuntu.com/community/RootSudo")
> By default, the root account password is locked in Ubuntu. This means that you cannot login as root directly or use the su command to become the root user.
So this would lead me to believe is the reason for no terminal.

---

### Post by Snowhog on 2009-05-03
Then why did the dev's leave the Item in the menu to be selected? Anything that is installed 'by default' should be usable.

---

### Post by danebramaged on 2009-05-03
> **Snowhog said:**
> I have the same issue. Hey guys, how about an answer? Root Terminal is a selectable Item under System Tools. It should then, when selected, work. But it does not. One is prompted for the users password, but no terminal starts up.

You have crystallized my thoughts exactly.  I am not the only one having this problem.

---

### Post by danebramaged on 2009-05-03
> **overdrank said:**
> Hi and from [RootSudo]("https://help.ubuntu.com/community/RootSudo")

Quote:
 	 	 		 By default, the root account password is locked in Ubuntu. This means that you cannot login as root directly or use the su command to become the root user. 


So this would lead me to believe is the reason for no terminal.

As I have already stated above, the password works.  I have no problem using the sudo command from a regular console.

When I go to use the root terminal, the system asks for the password.   I already know what the password is, and I type in the root password.

The system accepts the password because it is the correct password.  Do you get it?

Past the point at which the root password has been entered,  nothing happens.  Do you understand?

---

### Post by danebramaged on 2009-05-03
Here's something interesting:

When I right click on "Applications" and select "Edit Menu" and then click on "System Tools" then click on "Root Terminal" and then select "Properties", the actual command for starting "Root Terminal" is:

**gksu /usr/bin/x-terminal-emulator**

Furthermore:

If you try to uninstall "Root Terminal" you will be asked if you *really* want to remove "ubuntu-desktop". :confused:

NOT good.  :(

...ahem.

No, I do not want to remove Ubuntu-Desktop.  At the point which I have to remove the whole damn thing to fix a problem I might as well revert back to using microslop for an OS.

---

### Post by Wug on 2009-05-03
I am having the same problem.  Updated to 9.04, open root terminal yields password prompt, I enter correct password, then** nothing interesting happens.** Sudo continues to work normal(ish)ly (how do you resolve the error "unable to resolve host ~hostname~"?)

---

### Post by benny bronx on 2009-05-03
> No, I do not want to remove Ubuntu-Desktop. At the point which I have to remove the whole damn thing to fix a problem I might as well revert back to using microslop for an OS.


Ubuntu-desktop is just an empty metapackage that pulls in all the dependencies for the desktop, and may be safely removed if you are not planning on doing an upgrade, or reinstalled prior to an upgrade.

> The system accepts the password because it is the correct password. Do you get it?

Easy there cowboy, that there is the sheriff you're talking to.

---

### Post by danebramaged on 2009-05-03
:mrgreen: whups

:mrgreen: I think I need a support group.

...or perhaps a little luv from the community would be nice.   That, and a nice cup of Ah - BUN - too.

---

### Post by danebramaged on 2009-05-04
I've been digging around inside the log file viewer in the auth.log section and this is what happens when I try to start the root terminal from the Applications -  System Tools menu:

May  4 17:50:01 Monolith CRON[4827]: pam_unix(cron:session): session opened for user root by (uid=0)
May  4 17:50:01 Monolith dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.34" (uid=1000 pid=3983 comm="/usr/lib/indicator-applet/indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.81" (uid=0 pid=4827 comm="/USR/SBIN/CRON "))
May  4 17:50:01 Monolith CRON[4827]: pam_unix(cron:session): session closed for user root

Does this help at all?

I went to synaptic package manager and selected "Reinstall" because I am lacking in confidence at this point.  I really don't want to take 2 steps back.  Anyway, it made no difference.

---

### Post by montego95 on 2009-05-05
This is definitely a change in 9.04.  I just upgraded from 8.10 and now I have the same issue.  I have always been able to go from the Applications --> System Tools --> Root Terminal option and it would prompt me for the root password and then bring up a terminal as the root user.  

I would prefer to continue to maintain this feature of Ubuntu as having to type in "sudo" in front of everything when I can do just fine as root, is really annoying.  I prefer choice over Big Brother trying to protect me from myself.  I just have a feeling something was overlooked within the upgrade processing scripts.

---

### Post by Thouin on 2009-05-07
I'm having the same problem, has anyone been able to fix it?

---

### Post by Malac on 2009-05-07
+1

If I open a normal terminal then run ```
gksu /usr/bin/x-terminal-emulator
``` I get ```
Failed to contact the GConf daemon; exiting.
```

---

### Post by danebramaged on 2009-05-07
I just tried your command.

gksu /usr/bin/x-terminal-emulator
Failed to contact the GConf daemon; exiting.isaac@Monolith:~$ 
isaac@Monolith:~$ 

I get the same the thing. :confused:

Nobody seems to want to talk to us? :(

---

### Post by Malac on 2009-05-08
> **danebramaged said:**
> I just tried your command.

gksu /usr/bin/x-terminal-emulator
Failed to contact the GConf daemon; exiting.isaac@Monolith:~$ 
isaac@Monolith:~$ 

I get the same the thing. :confused:

Nobody seems to want to talk to us? :(
There is a launchpad bug which has been triaged but is set at 'Low' priority
[https://bugs.launchpad.net/ubuntu/+source/gconf2/+bug/328575](https://bugs.launchpad.net/ubuntu/+source/gconf2/+bug/328575)

plus a duplicate:
[https://bugs.launchpad.net/ubuntu/+bug/326158](https://bugs.launchpad.net/ubuntu/+bug/326158)

---

### Post by oldos2er on 2009-05-08
This (Failed to contact the GConf daemon; exiting) also happens when I try to run "sudo gnome-terminal" or "gksu gnome-terminal". Very annoying.

---

### Post by danebramaged on 2009-05-08
> **Malac said:**
> There is a launchpad bug which has been triaged but is set at 'Low' priority
[https://bugs.launchpad.net/ubuntu/+source/gconf2/+bug/328575](https://bugs.launchpad.net/ubuntu/+source/gconf2/+bug/328575)

plus a duplicate:
[https://bugs.launchpad.net/ubuntu/+bug/326158](https://bugs.launchpad.net/ubuntu/+bug/326158)

very iluminating ...

... hmmm

---

### Post by maciu on 2009-05-13
I am having the same problem from February (since i switched to Jaunty), as you guys said the bug has a low priority on Launchpad, and there is 100 duplicates of it, i dont know what else should the users to in order to get t fixed. :(

---

### Post by ChaiTan on 2009-05-13
I'm using a workaround for this:
```
gnome-terminal -e "sudo -i"
```

---

### Post by danebramaged on 2009-05-13
i can sudo from a standard terminal no problem.

What nobody seems to be able to do is to actually use the root terminal that jackalope installs into the menu by default.  One would think that a default menu item for the distro in question would have been properly tested.  As per the lauchpad discussion, it's an insidious problem and apparently one that is not easily fixed.  They have known about it since about January.

I am actively looking at other distros to see which one bytes the very least.  I have solved all but three of my problems so far, (thank you Ubuntu Forums People) but each of the remaining ones is just annoying as hell considering that 8.04 and 8.10 did not outwardly exhibit any of these problems.

...oh well.

---

### Post by curts on 2009-05-15
Thanks for the workaround.  I've dropped into an alias for convenience.
```
alias suterm='gnome-terminal -e "sudo -i"'
```
Sometimes sudo just doesn't do the job and this has been driving me nuts since upgrading from 8.10 to 9.04.

---

### Post by meganox on 2009-05-18
I don't see why anyone would want to start an xterm as root.  Much safer to leave a normal user terminal running and "sudo -i" into a root shell when you need it.

---

### Post by danested on 2009-05-25
HI i face the same problem but i found a way to avoid being stopped being root... 

$ sudo passwd
Enter new UNIX password:

with this you can set the root password..
then su to get a root shell with your new unix password...

PS: You can use sudo nautilus to open a new nautilus browser with root privillages(closes if terminal is closed):popcorn:

---

### Post by presence1960 on 2009-05-25
it is recommended that one use gksu instead of sudo for graphical root applications such as nautilus.

---

### Post by Malac on 2009-05-26
> **meganox said:**
> I don't see why anyone would want to start an xterm as root.  Much safer to leave a normal user terminal running and "sudo -i" into a root shell when you need it.
I do a lot of programming and similar stuff and being able to right-click on a folder in a gksu'ed root nautilus and choose Open in Terminal to give a 'root' terminal was convenient.
This is not a 'major bug', it is more of an annoyance having to open a terminal sudo -i it then type in the folder path to cd to (which can be over 50 characters long in my case).
Especially as this has always been available in every other Ubuntu released up to 9.04.

---

### Post by noSelf on 2009-06-03
thanks for the workaround!

---

