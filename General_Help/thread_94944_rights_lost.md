---
title: "rights lost"
date: 2005-11-25
forum: General Help
---

### Post by RobertLos on 2005-11-25
Hi,

Worked for some time now with ubuntu breeze badger 5.10 - to my full satisfaction. Got everything to run within a few minutes. Since last week I got a nasty problem. Firefox will only show pages which are local (via my apache2 webserver) and crashes when connecting to another site when I am not root (I have to start firefox with 'sudo firefox &' to get a working web browser.
Also my eclipse environment only works when started from a command prompt using 'sudo eclipse &'. Otherwise it crashes with

JVM terminated. Exit code=1
/usr/bin/java
-cp /opt/eclipse/startup.jar org.eclipse.core.launcher.Main
-os linux
-ws gtk
-arch x86
-showsplash /opt/eclipse/eclipse -showsplash 600
-exitdata /opt/eclipse/eclipse -exitdata d0013
-vm /usr/bin/java
-vmargs
-cp /opt/eclipse/startup.jar org.eclipse.core.launcher.Main

All applications started in the system->administration module crash as soon as the root password is entered in the dialogue box.

There seems to be something wrong with my user credentials or java or something else.
Things started to go wrong after installing clamAV. Removing clamAV did not solve the problem.

Any idea's.

thanks

Robert

---

### Post by teaker1s on 2005-11-25
I know root is disabled on gui login but as prompt login someone may be able to tell you how to login as root and create a new administrator account with sudoer privileges. 
please report your issue in link below as I have a similar problem

[https://launchpad.net/distros/ubuntu/+bug/4738]("https://launchpad.net/distros/ubuntu/+bug/4738")

---

### Post by RobertLos on 2005-11-25
Thanks Teaker1s,

The problem is not that I don't know how to sudo or login as root. This works just fine. the problem is that I cannot use some normal applications like mozilla-firefox or the eclipse IDE without being root. Some directory or service seems to have forgotten that I (as a normal user) have the right to use the application.
A side effect is that the sudo box which appears when I select e.g. the synaptic package manager or any other application in the System->administration menu crashes as soon as i start typing the sudo password.

:( 

Robert

---

### Post by teaker1s on 2005-11-25
same as me what has happened is your account priviliges have changed same bug I have unless you have another account you can login with gnome then you will need someone to tell you how to go about editing in text mode as root

Sorry I can't be more helpful.

---

### Post by teaker1s on 2005-11-25
okay figured out how you can fix it if sudo works in konsole
print this first so you have a copy
in console 
sudo passwd root
(your login password)
(root password)
(retype root password)

keep root password safe as you are stopped from login graphically and normally as root can destroy system if you get it wrong

next log out and on login options select console login
root
password

 type 'startx'
you should be in root desktop 
system-administration-users and groups
select a your login and properties
next select user privileges and tick all boxes
before we leave create a new user by clicking add user
after you have filled the first section hit the advanced tab and change profile to administrator next hit user privileges and check all boxes have ticks
log out
type reboot
login as normal or if it's still problem use new login we created

---

### Post by RobertLos on 2005-11-26
Thanks, Tried that and gave myself rights on all the boxes. When I give other users all rights everything seems to work just fine. Just not my own account.

Robert

---

### Post by teaker1s on 2005-11-26
glad that worked, hopefully the bug will get sorted, another way to bypass this is to add the affected items to panel or desktop and start them with either 'sudo' or if that doesn't work use 'gksudo' command

If you find this bug unbearable i would suggest copy your important files to another login account home folder using the command 'gksudo nautilus' you will have to click and change permissions on files and folders if you move them

---

