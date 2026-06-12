---
title: "DStar DVDongle Ham Radio Install Instructions"
date: 2008-02-22
forum: Hardware &amp; Laptops
---

### Post by GalloGlas on 2008-02-22
Ubuntu Linux contains native drivers that support the DVDongle.  However, actually getting the DV Tool to work can be a little nerve racking if you haven't taken the appropriate steps. 

The following is what I did in order to start using D-Star.   


Step one:  

Remove any brltty or any other Braille addons you have installed.  You can easily do this by search "braille" in your synaptic package manager and mark every install to be removed.   

Step two: 

Remove any and all Java installs. (don't worry, we are about to replace java)   


Step three: 

Open a terminal and enter the following  

```
  
sudo apt-get install sun-java6-bin sun-java6-jre 
```

Now you've installed the latest java that is needed for the DV Tool to run correctly but you're not done yet.   

You've got to edit /etc/jvm  

```
 
sudo gedit /etc/jvm 
```   

Make sure you have the following at the top of the list:
```

/usr/lib/jvm/java-6-sun 
```

Once you've made the change, save and close the file.    

Now you've got to setup your Environmental Variable. 

In the terminal again 
```
 
sudo gedit /etc/profile 
```  

right above the very last line insert the following: 

```
 
export JAVA_HOME=/usr/lib/jvm/java-6-sun
export PATH=$PATH:$JAVA_HOME/bin 
```   


Now lets make sure everything is correct.  

```

java -version 
```

If the following does not look exactly like this your DV Tool will not work and you will not be able to use the DV Dongle   

```

java version "1.6.0_03"
Java(TM) SE Runtime Environment (build 1.6.0_03-b05)
Java HotSpot(TM) Client VM (build 1.6.0_03-b05, mixed mode, sharing)

```

Next , go to the DV Dongle website and download the free DV TOOL:

[http://www.dvdongle.com/downloads/DVTool-dist.tgz](http://www.dvdongle.com/downloads/DVTool-dist.tgz) 

Unpackage the file to a folder on your desktop.  

You cannot run DVTool.jar directly and have your DV Dongle work.  First, plug in the DV Dongle and then open DVTool.sh.

Once it starts, you should see something along the lines of dev/tty/usb0 or something similar in the drop down box.   If not, you may have a problem with linux seeing your USB ports.  There should be a couple of posts on the Ubuntu Forums about fixing USB problems.   
 
Click on open next to that drop down box to access the DV Dongle. 

 The second section should un-grey and you should be able to click on the "Connect to Gateway" button and have a selection of different Dstar Nodes pop up in the drop down box. 

Thats it, you're up and running!

---

### Post by joey on 2008-02-27
Way cool, thanks!

---

### Post by GalloGlas on 2008-02-27
No problem.   Glad I could help!  

KI4WIC

---

