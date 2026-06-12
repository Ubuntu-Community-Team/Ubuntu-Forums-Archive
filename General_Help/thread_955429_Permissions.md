---
title: "Permissions"
date: 2008-10-22
forum: General Help
---

### Post by hndaklr8480 on 2008-10-22
Hello,  I am new to Ubuntu, and even though it is a little difficult to learn stuff, I am always up to learning and a challenge.  Not sure if this is the right place to post if not I am sorry.

My Question is, I installed Ubuntu on my computer, I have installed what ever programs that are extra and not included. Not all of them work. Troubleshooting is the challenge, But what makes it really hard is while troubleshooting and getting help online it is hard to follow instruction when about 75% of the thing i have to do require permission.  I am the one and only user of this computer so on the desktop when i am logged in, I don't understand why I don't have permission to everything.  Is there a way to solve this once and for all.  I want to have access to my whole computer when i log in not have to goto terminal and chmod commands to grant access to things. is this possible.  I installed planeshift and have to got to terminal and sudo planeshift just to play. It is really frustrating not to have access to my own computer.  thanx for any help

---

### Post by baju on 2008-10-22
You don't have access to everything to protect you from damaging your system. I think nobody in this forum will encourage you to log in as root.
If planeshift is not working without root privileges, you will propably have to change the permissions of the gamefiles using chmod and chown or ask in their forum for help.

---

### Post by geirha on 2008-10-22
> **baju said:**
> You don't have access to everything to protect you from damaging your system. I think nobody in this forum will encourage you to log in as root.
If planeshift is not working without root privileges, you will propably have to change the permissions of the gamefiles using chmod and chown or ask in their forum for help.

+1

It's better to learn how permission and ownership work, and use them to fit your needs. 

Here's a couple of google searches to get you started:
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[http://www.tuxfiles.org/linuxhelp/filepermissions.html](http://www.tuxfiles.org/linuxhelp/filepermissions.html)

---

### Post by Kevbert on 2008-10-22
Permissions are there so that Ubuntu is secure. That's why it's promoted as being free from viruses, malware, spyware, unlike a basic install of Windows which is open for anyone and everyone to change as they see fit.

---

### Post by notnic on 2008-10-22
I think I might of made the same mistake but I know why. When I installed the game, I ran it as root and placed it in the root-home folder. I need to run the uninstaller but dont know how. sudo planeshift plays the game. Can anyone help me?

---

### Post by baju on 2008-10-22
I guess you have to run the uninstaller with sudo, too. However, please open a new thread, since this one has a different topic.

---

