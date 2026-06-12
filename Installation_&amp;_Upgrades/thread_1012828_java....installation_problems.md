---
title: "java....installation problems"
date: 2008-12-16
forum: Installation &amp; Upgrades
---

### Post by nikhilneela on 2008-12-16
hello everyone!!!I am new to Ubuntu and i tried to install java using the following command....sudo apt-get install openjdk-6-jdk sun-java6-jdk.i did not know what was happening(since terminal was idle after downloading reached to 100%).so i closed terminal.from then i am unable to install java.I get this kind of error.......

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

please help me out.plz.

---

### Post by taurus on 2008-12-16
Open a terminal and run

```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by nikhilneela on 2008-12-18
Hi everyone,
             I tried to install java5 using the following command
              sudo apt-get install sun-java5-jdk....after completing 100% download,I closed terminal thinking that installation has finished....from then onwards i am unable to install any new package....i am getting error like this...."E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem."........please help me out....
              thanks

---

### Post by taurus on 2008-12-18
Open a terminal and run

```
sudo dpkg --configure -a
sudo apt-get update
```

p.s.  When you install java (version from Sun), you have to accept licensing.  That's why you get that error message because you shut it down before it was really completed.

---

### Post by lovelyvik293 on 2008-12-18
Use 
```
dpkg --configure -a
```

---

### Post by nikhilneela on 2008-12-18
sorry to trouble u.......but i still get these errors

E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

by the way what is root????

---

### Post by taurus on 2008-12-18
```
**sudo** apt-get -f install
```
Should stick with your original post instead of creating a new one!

[http://ubuntuforums.org/showthread.php?t=1014907](http://ubuntuforums.org/showthread.php?t=1014907)

---

### Post by linux_tech on 2008-12-18
when you install java, you need to use the tab and enter keys to make the selections.  ie. tab to selection, should highlight in red, then press enter key.

---

### Post by nikhilneela on 2008-12-18
hey please help me out friends..........
when i try to install java using the command.."sudo apt-get install sun-java5-jdk"  I am getting this error..."E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution)." And when i type "apt-get -f install" I am getting this kind of error.. 

"E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?"

  what is all this?I am a beginner to Ubuntu....Please please help me out.....I Deliberately need java...please help me out..
 thanks

---

### Post by securitynut on 2008-12-18
Try installing via the repositories. In the terminal type: sudo gedit /etc/apt/sources.list.

It will bring up the repositories for your system. Go to the bottom of the list and add: 

    * deb [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) intrepid main restricted
    * deb [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) intrepid multiverse

If you are using hardy or gusty, put them in place of intrepid. 

Save sources.list then go to the terminal and type: sudo apt-get update

After that runs type: sudo apt-get install sun-java6-jre sun-java6-jdk sun-java6-plugin 

(Replace the 6 if you need version 5).

Finally type: java -version to make sure it installed.

---

### Post by taurus on 2008-12-18
Why do you keep creating a new thread when the problem you have is the same or related?

[http://ubuntuforums.org/showthread.php?t=1014920](http://ubuntuforums.org/showthread.php?t=1014920)
[http://ubuntuforums.org/showthread.php?t=1014907](http://ubuntuforums.org/showthread.php?t=1014907)

Can you at least stick to one thread?

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by bapoumba on 2008-12-20
3 threads merged in.

---

