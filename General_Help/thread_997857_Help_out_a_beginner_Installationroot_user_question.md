---
title: "Help out a beginner: Installation/root user questions"
date: 2008-11-30
forum: General Help
---

### Post by bmold on 2008-11-30
Hi everyone, 

I suppose this is probably a dumb question, I am very new to Unix/ Ubuntu in general and am recently trying to make the switch (from windows). I am located in China right now, and in order to access the wired network at my school we have to install a program called "racer" (see link: [http://218.29.0.252/kuandai/self.jsp](http://218.29.0.252/kuandai/self.jsp)), the first link under the linux section, that allows us to connect to the internet provider. I downloaded and decompressed the tar/gz file but I'm not exactly sure what to do after that.. 

Basically my questions are
 
-what is a root user
-... basically, how do I go about installing this program?
-how do I become/do stuff as the root user? (and is this dangerous? I don't want to change critical things as the root user and then mess everything up.)
- Thanks!

Hope my questions aren't too stupid.

Here are the instructions for installing the program (they came with the file as a readme file:

1. It is necessary to have root privileges in order to use this client to access the network. Confirm the dhcp module (dhcpcd) have been installed on your Linux OS and the network interface have been set up to "use dynamic IP config". The version of C share lib in system is more than 2.3.

2. Install: Extract the installing file to the path denoted by $dest_path. $dest_path should be used below, and should be changed to the actual value when you use it. Then it is OK.

3. Environment setting: Environment variable RACERC=$dest_path should be added to the root user, and $dest_path should be added to PATH environment variable of root user.

4. Config: Edit the racer.ini to modify the value of server 1 and server 2. Server 1 and server 2 mean IP address of the server. Server 1 and server 2 should be set to one single IP if there is only one single IP address.

5. User's guide: 

Logon: $dest_path/racer/econ.sh     start
check status: $dest_path/racer/econ.sh     status
logoff: $dest_path/racer/econ.sh     stop

---

### Post by Diabolis on 2008-11-30
One of many guides available in the internet about installing software in Ubuntu: [http://ubuntuforums.org/showthread.php?t=500020](http://ubuntuforums.org/showthread.php?t=500020)

You execute a command as the root user by prepending the command **sudo**. Example:
```
sudo mkdir aRootDir
```
*Creates a folder called aRootDir as the root user, so root owns the folder and is the only one who can modify it. Permissions are more complex than that, but thats a beginning.*

---

### Post by drs305 on 2008-11-30
To temporarily achieve administrative rights, you preface a command with either 'sudo' for terminal operations (for example, blkid) or 'gksudo' for operations which will initiate a graphical interface (e.g. nautilus).

When you use sudo or gksudo, you will be asked to enter your password. You won't see anything as you type but it will be registered. Just hit ENTER when you have finished typing.

Here are a couple of links to help explain things.
Administrative Tasks & Sudo:
[Administrative Tasks]("https://help.ubuntu.com/7.04/administrative/C/")

Sudo:
[RootSudo]("https://help.ubuntu.com/community/RootSudo")

sudo vs. gksudo:
[graphicalsudo]("http://www.psychocats.net/ubuntu/graphicalsudo")

---

