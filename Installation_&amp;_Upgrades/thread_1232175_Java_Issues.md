---
title: "Java Issues"
date: 2009-08-05
forum: Installation &amp; Upgrades
---

### Post by RickWolford on 2009-08-05
I get these messages when I try and install the updated version of Java

This one first

[IMG]http://i46.photobucket.com/albums/f104/LiSyaoran3063/Prob01.png[/IMG]

This one second

[IMG]http://i46.photobucket.com/albums/f104/LiSyaoran3063/Prob02.png[/IMG]

What do I need to do? Youtube REALLY bogs down my computer, and so browse buttons just don't exist anymore >.>

---

### Post by Mighty_Joe on 2009-08-05
It sounds like you need to browse to [http://java.sun.com/javase/downloads](http://java.sun.com/javase/downloads), download a file named jdk-6u10-docs.zip, put it in the tmp directory and change the owner to root.
Did you try just typing in "NO"?  The sun-java6-jdk package makes it sound like the docs are optional.

---

### Post by RickWolford on 2009-08-05
> **Mighty_Joe said:**
> It sounds like you need to browse to [http://java.sun.com/javase/downloads](http://java.sun.com/javase/downloads), download a file named jdk-6u10-docs.zip, put it in the tmp directory and change the owner to root.
Did you try just typing in "NO"?  The sun-java6-jdk package makes it sound like the docs are optional.
Yeah I did. Nothing happens, and says there was an error in updating. Ill try that and see what I can find.

---

### Post by Mighty_Joe on 2009-08-05
There's also a sun-java6-docs (or something like that, I'm using XP right now) package available.  Maybe try to install that at the same time?

---

### Post by RickWolford on 2009-08-06
> **Mighty_Joe said:**
> There's also a sun-java6-docs (or something like that, I'm using XP right now) package available.  Maybe try to install that at the same time?
Maybe. Which one do I DL on the link you gave me. 2 of them were like (can't open). Im assuming because its for windows? I just started with Linux so forgive my ignorance

---

### Post by Mighty_Joe on 2009-08-07
That's very odd. Let's try it step by step:
- Open [this link]("http://java.sun.com/javase/downloads/index.jsp#docs") in a new window.
- Next to the words "Java SE 6 Documentation", click on the orange button that says "Download"
- You will go to a page with form labeled "Select Platform and Language for your download:".  Click on the second drop-down and select "English". Click on the check box labeled "I agree to the Java SE Development Kit Documentation 6 License Agreement".
- Click the orange "Continue" button.
- You will go to another page.  In the middle of the page there is the text "Required Files". Under that is a blue-gray bar marked "File Description and Name". Under that is a white box.  Inside the white box is a checkbox labeled "Java SE Development Kit Documentation 6".  Under that is a hyperlink "jdk-6u10-docs.zip".  Click on the hyperlink.  You will be prompted to save the file.  Save it somewhere.
- Copy the file to the /tmp directory
- Change the owner to root:
```
sudo chown root jdk-6u10-docs.zip
```
- now try to install the sun-java6-jre package through Synaptic.

---

### Post by RickWolford on 2009-08-10
> **Mighty_Joe said:**
> That's very odd. Let's try it step by step:
- Open [this link]("http://java.sun.com/javase/downloads/index.jsp#docs") in a new window.
- Next to the words "Java SE 6 Documentation", click on the orange button that says "Download"
- You will go to a page with form labeled "Select Platform and Language for your download:".  Click on the second drop-down and select "English". Click on the check box labeled "I agree to the Java SE Development Kit Documentation 6 License Agreement".
- Click the orange "Continue" button.
- You will go to another page.  In the middle of the page there is the text "Required Files". Under that is a blue-gray bar marked "File Description and Name". Under that is a white box.  Inside the white box is a checkbox labeled "Java SE Development Kit Documentation 6".  Under that is a hyperlink "jdk-6u10-docs.zip".  Click on the hyperlink.  You will be prompted to save the file.  Save it somewhere.
- Copy the file to the /tmp directory
- Change the owner to root:
```
sudo chown root jdk-6u10-docs.zip
```- now try to install the sun-java6-jre package through Synaptic.
[IMG]http://i46.photobucket.com/albums/f104/LiSyaoran3063/Screenshot.png[/IMG]

---

### Post by a2z on 2009-08-13
> **Mighty_Joe said:**
> That's very odd. 
- Copy the file to the /tmp directory
- Change the owner to root:
```
sudo chown root jdk-6u10-docs.zip
```
- now try to install the sun-java6-jre package through Synaptic.

excellent! thanks Mighty _Joe!
Thank you, 

a2z

---

### Post by Mighty_Joe on 2009-08-14
@a2z: Kudos!
@RickWolford: It looks like you have Firefox set up to open zip files with some application and that application is missing (sorry it took me so long, I'm on vacation).  When I download files, including the Java Documentation, it just saves the file to disk.  It does not try to open the file.
First, just check to see if the file is in the /tmp directory.  It sounds like it downloaded fine, but Firefox couldn't open it.  If the file is there, change the owner and try to install Java.
If the file isn't there, try changing the download setting. In Firefox, click on the Edit menu, click on Preferences, then click on the Applications tab.  If there is a setting for zip files, try changing the drop-down box next to it to "Always Ask".  When you download the file above, it should prompt you to save the file or to open it.  Save it.

---

### Post by moredocx on 2009-08-17
I'm a total newbie in Ubuntu. Can someone help me pls? I tried to install Java, but my PC crashed. After restarting, I got this message when I tried installing again.

Reading package lists... Done                                                                                                                     
Building dependency tree                                                                                                                          
Reading state information... Done                                                                                                                 
gsfonts-x11 is already the newest version.                                                                                                        
java-common is already the newest version.                                                                                                        
odbcinst1debian1 is already the newest version.                                                                                                   
sun-java6-fonts is already the newest version.                                                                                                    
sun-java6-plugin is already the newest version.                                                                                                   
unixodbc is already the newest version.                                                                                                           
The following NEW packages will be installed:                                                                                                     
  sun-java6-bin sun-java6-jre                                                                                                                     
0 upgraded, 2 newly installed, 0 to remove and 4 not upgraded.                                                                                    
6 not fully installed or removed.                                                                                                                 
Need to get 35.5MB of archives.                                                                                                                   
After this operation, 101MB of additional disk space will be used.                                                                                
Get:1 [http://archive.mmu.edu.my](http://archive.mmu.edu.my) jaunty-updates/multiverse sun-java6-bin 6-14-0ubuntu1.9.04 [29.1MB]                                               
Get:2 [http://archive.mmu.edu.my](http://archive.mmu.edu.my) jaunty-updates/multiverse sun-java6-jre 6-14-0ubuntu1.9.04 [6421kB]                                                         
Fetched 35.5MB in 4min 43s (125kB/s)                                                                                                                        
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable                                    
(Reading database ... 124128 files and directories currently installed.)                                                                                    
Unpacking sun-java6-bin (from .../sun-java6-bin_6-14-0ubuntu1.9.04_i386.deb) ...                                                                            
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable                                    
dpkg: error processing /var/cache/apt/archives/sun-java6-bin_6-14-0ubuntu1.9.04_i386.deb (--unpack):                                                        
 subprocess pre-installation script returned error exit status 1                                                                                            
Unpacking sun-java6-jre (from .../sun-java6-jre_6-14-0ubuntu1.9.04_all.deb) ...                                                                             
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable                                    
dpkg: error processing /var/cache/apt/archives/sun-java6-jre_6-14-0ubuntu1.9.04_all.deb (--unpack):                                                         
 subprocess pre-installation script returned error exit status 1                                                                                            
Errors were encountered while processing:                                                                                                                   
 /var/cache/apt/archives/sun-java6-bin_6-14-0ubuntu1.9.04_i386.deb                                                                                          
 /var/cache/apt/archives/sun-java6-jre_6-14-0ubuntu1.9.04_all.deb                                                                                           
E: Sub-process /usr/bin/dpkg returned an error code (1)


Then I ran this command:

sudo apt-get clean
sudo apt-get -f install

I still get the same message. What should I do?

---

### Post by Mighty_Joe on 2009-08-18
> **moredocx said:**
> I'm a total newbie in Ubuntu. Can someone help me pls? I tried to install Java, but my PC crashed. After restarting, I got this message when I tried installing again.


Your problem has nothing to do with Java (other than the fact you're trying to install it).  A google search led me to [this bug ]("https://bugs.launchpad.net/ubuntu/+source/fontconfig/+bug/271246") where someone says:
> This was due to a concurrent access to the debconf database. This is usually a very temporary and not reproducible situation. If you can reproduce it then use the following command to find the culprit:
fuser -v /var/cache/debconf/config.dat
The fuser command will show which processes are using a specified file.  Presumably there's a conflict over that file and you need to terminate the other applications.

---

### Post by Richiegs on 2009-10-20
Under that is a hyperlink "jdk-6u10-docs.zip".  Click on the hyperlink.  You will be prompted to save the file.  Save it somewhere.
- Copy the file to the /tmp directory
- Change the owner to root:
```
sudo chown root jdk-6u10-docs.zip
```
- now try to install the sun-java6-jre package through Synaptic.[/QUOTE]

1) How do I copy jdk-6u10-docs.zip into /tmp directory?
   I tried **sudo cp jdk-6u10-docs.zip /tmp**, it said **cp: cannot stat `jdk-6u10-docs.zip': No such file or directory**

Please help.

---

### Post by stumbleUpon on 2009-10-20
> **Richiegs said:**
> 
1) How do I copy jdk-6u10-docs.zip into /tmp directory?
   I tried **sudo cp jdk-6u10-docs.zip /tmp**, it said **cp: cannot stat `jdk-6u10-docs.zip': No such file or directory**

Please help.

Where did save the file..? Navigate to that folder and copy it to the /tmp directory.

---

### Post by Mighty_Joe on 2009-10-20
> **Richiegs said:**
> 
Please help.

I answered your question after your [other post]("http://ubuntuforums.org/showthread.php?p=8134248#post8134248"). 
Please do not post the same question more than once.  It causes confusion and duplication of effort.

---

### Post by ITT1 on 2010-02-24
> **Mighty_Joe said:**
> That's very odd. Let's try it step by step:
- Open [this link]("http://java.sun.com/javase/downloads/index.jsp#docs") in a new window.
- Next to the words "Java SE 6 Documentation", click on the orange button that says "Download"
- You will go to a page with form labeled "Select Platform and Language for your download:".  Click on the second drop-down and select "English". Click on the check box labeled "I agree to the Java SE Development Kit Documentation 6 License Agreement".
- Click the orange "Continue" button.
- You will go to another page.  In the middle of the page there is the text "Required Files". Under that is a blue-gray bar marked "File Description and Name". Under that is a white box.  Inside the white box is a checkbox labeled "Java SE Development Kit Documentation 6".  Under that is a hyperlink "jdk-6u10-docs.zip".  Click on the hyperlink.  You will be prompted to save the file.  Save it somewhere.
- Copy the file to the /tmp directory
- Change the owner to root:
```
sudo chown root jdk-6u10-docs.zip
```
- now try to install the sun-java6-jre package through Synaptic.

I've followed tthe directions, but the version available on the site is now 6u18. Can I:
a. rename the file to 610 or
b. change the synaptic settings to use the new version of the zip file?

thanks

---

### Post by Mighty_Joe on 2010-02-25
You could probably just rename the file and everything would be fine.  The documentation package is just a bunch of HTML files and images so I don't think there would be a problem.
If you want to install the latest version of Java, you'll have to follow [this procedure]("http://sites.google.com/site/easylinuxtipsproject/java") as Sun Java is not being updated in the Karmic repository.

---

### Post by ITT1 on 2010-02-26
> **Mighty_Joe said:**
> You could probably just rename the file and everything would be fine.  The documentation package is just a bunch of HTML files and images so I don't think there would be a problem.
If you want to install the latest version of Java, you'll have to follow [this procedure]("http://sites.google.com/site/easylinuxtipsproject/java") as Sun Java is not being updated in the Karmic repository.

Worked. Thanks!

---

