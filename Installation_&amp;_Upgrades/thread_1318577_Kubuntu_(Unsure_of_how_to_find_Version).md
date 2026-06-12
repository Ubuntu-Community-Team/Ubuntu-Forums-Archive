---
title: "Kubuntu (Unsure of how to find Version)"
date: 2009-11-07
forum: Installation &amp; Upgrades
---

### Post by Saito Chikara on 2009-11-07
So, anyways, i downloaded and installed the, I presume, newest version of Kubuntu, and I was trying to figure out how to install BitDefender (BitDefender-Antivirus-Scanner-7.6-4.linux-gcc4x.amd64.deb.run) and I was at a complete loss as to how to do so. I'm not really adept at coding, but I'm fed up with Windows, and too poor to afford a Mac. So, can anyone help me?

Oh, when i try to do a 

"sudo dpkg" command on it, it keeps telling me that I need Superuser Privileges. How do I get that? I'm the only user on this computer, and I'm using the account I made on install, so I'm at a loss. (Still used to the windows interface.)

I also used the tutorial at [https://help.ubuntu.com/community/InstallingRunPackage]("https://help.ubuntu.com/community/InstallingRunPackage") and still, get the superuser message.

Any help is appreciated!

Thanks!

~Saito

---

### Post by stlsaint on 2009-11-07
in terminal become root: 
```
sudo -i
```

enter your password, it will not show any characters but enter it anyway and push enter, then try and run cmd.

---

### Post by Saito Chikara on 2009-11-07
tried that too. Still I get the Superuser message.

---

### Post by coffeecat on 2009-11-07
I think you need to post **exactly** what you typed into the terminal when you got the superuser message, and post the **exact and complete** message about superuser privileges.

I'm mystified because if you use sudo in a terminal and type your password in correctly, you gain superuser (root) privileges. Also if you type 'sudo -i' as stisaint suggested, the terminal prompt will change from a '$' to a '#', signifying that you now have root privileges and you should exercise care. (You can completely destroy a system with very little effort once you gain root powers.)

You might find this useful:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

**Edit:** just remembered about that bitdefender package which is a bit odd. You can't use dpkg with it. Make sure you've made it executable as instructed in that link you gave. Now open a terminal and cd to the directory where you've stored the BitDefender*.run package. Now:

```
sudo -i
```

Put your password in. Now:

```
./BitDefender-Antivirus-Scanner-7.6-4.linux-gcc4x.amd64.deb.run
```

I've copied and pasted BitDefender from your post. It has to be exactly right - no uppercase/lowercase substitutions - Linux is case sensitive. The easiest way is to type './BitD', followed by the tab key and it will autocomplete. Press enter and the package should autorun with root powers.

---

### Post by Saito Chikara on 2009-11-07
I just lost the tutorial page I was using... 

I am pretty sure I went 

sudo -s

sudo -i BitDefender-Antivirus-Scanner-7.6-4.linux-gcc4x.amd64.deb.run


I'm not 100% sure, but I think that was close. I hate it when Konqueror crashes and I loose my tabs...

EDIT- 

How do I Change Directories? I believe the file is on the desktop..

---

### Post by coffeecat on 2009-11-07
> **Saito Chikara said:**
> sudo -i BitDefender-Antivirus-Scanner-7.6-4.linux-gcc4x.amd64.deb.run

That won't work. First you need to do 'sudo -i' <enter> and put in your password to get root powers. And then you need to run the *run package prefixed with './' - see my edit to my last post. You have to be in the same directory as the package, and the './' tells the bash shell that you're running a script in the same directory.

**Edit:**

> EDIT- 

How do I Change Directories? I believe the file is on the desktop..

```
cd Desktop
```

---

### Post by Saito Chikara on 2009-11-07
> **coffeecat said:**
> That won't work. First you need to do 'sudo -i' <enter> and put in your password to get root powers. And then you need to run the *run package prefixed with './' - see my edit to my last post. You have to be in the same directory as the package, and the './' tells the bash shell that you're running a script in the same directory.

**Edit:**



```
cd Desktop
```
root@Kubuntu1:~# cd desktop
-bash: cd: desktop: No such file or directory


I'm sorry for being such a n00b and not knowing what the hell I'm doing, letalone doing wrong...

---

### Post by jacksaff on 2009-11-07
Since you have now become the root user you need to cd to /home/YOUR(NOT ROOT)USERNAME/Desktop to get to where you have the file.
It's easier and better to cd to the correct directory first as a normal user and just run the one command as root using sudo.

cd Des [TAB] [RETURN]
ls [RETURN]         (will tell you the contents of the directory so you can check you're in the correct place)
sudo ./BitD [TAB]     read the command line and check it's correct before hitting [RETURN]

---

### Post by Saito Chikara on 2009-11-07
cd /home/*****/Desktop
*****@Kubuntu1:~$ cd /home/*****/Desktop
*****@Kubuntu1:~/Desktop$ sudo -i
[sudo] password for *****:
root@Kubuntu1:~# cd /home/*****/Desktop
root@Kubuntu1:/home/*****/Desktop# ls
BitDefender-Antivirus-Scanner-7.6-4.linux-gcc4x.amd64.deb.run
root@Kubuntu1:/home/*****/Desktop# sudo ./BitDefender-Antivirus-Scanner-7.6-4.linux-gcc4x.amd64.deb.run
sudo: ./BitDefender-Antivirus-Scanner-7.6-4.linux-gcc4x.amd64.deb.run: command not found

---

### Post by Saito Chikara on 2009-11-07
What am I doing wrong? Why isn't it working?

Why isn't there an easy way to get things working?

---

### Post by coffeecat on 2009-11-08
> **Saito Chikara said:**
> What am I doing wrong?

You used sudo unnecessarily after you had escalated to root with 'sudo -i'. I don't think that will work. Also, did you make the BitDefender*.run file executable? It won't work if it isn't executable. This was described in the link that you gave in your first post.

In retrospect the suggestion to use sudo -i was unfortunate, because that lands you up in root's directory and you have to navigate back to your own desktop as jacksaff describes - which complicates things. Try this, four steps using 'sudo su' instead of 'sudo -i' and I've included a terminal command to get that file executable just in case.  

```
cd Desktop
sudo su
chmod +x BitDefender-Antivirus-Scanner-7.6-4.linux-gcc4x.amd64.deb.run
./BitDefender-Antivirus-Scanner-7.6-4.linux-gcc4x.amd64.deb.run
```

---

### Post by Saito Chikara on 2009-11-08
Seems to be working until i finish the EULA... It seems I have the wrong version for my PC. :/ Downloading the other version and hoping it works.

EDIT

Downloaded the i586 package and it seems to be running now. Thank you so much! I'm compiling a text document with all these commands so when I go to install this stuff on my wife's laptop, it'll all be good.

Thanks so much! 

SOLVED

---

