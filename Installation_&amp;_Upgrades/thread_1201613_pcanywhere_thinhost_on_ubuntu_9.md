---
title: "pcanywhere thinhost on ubuntu 9"
date: 2009-07-01
forum: Installation &amp; Upgrades
---

### Post by mayallma on 2009-07-01
Hi All,

First post for me and hopefully I can get some help! I use pcAnywhere 12.5 on Windows and Macs, but have been unable to get the pcathinhost to run on ubuntu. I was able to install pcAnywhere Cross Platform with some help from the forums here, but can not understand why the pcathinhost will not launch. It doesn't give any errors when I click launch, so one would think it has launched. Typically in Windows or on a Mac, it will display an icon in the system tray (Windows) or in the dock (Mac) to indicate the host is running. Doesn't do this on ubuntu; however, that doesn't mean it should. Someone posted libmotif3 wasn't installed and it should fix it. I installed through synaptics, but this did not resolve the problem. I went to the properties of both the ./pcathinhost and ./pcanywhere and they are both set to open with 'wine windows program loader'. I changed to open with 'sun java 6 web start', but this didn't change anything. Not sure if I am heading in the right direction or not. I can bring up the pcAnywhere ThinHost Configuration Tool, put in the credentials, but when I click 'launch', the window disappears and nothing happens. I have verified the thinhost isn't running by scanning for hosts on another computer running pcAnywhere. It sees my Mac and other computers, but not ubuntu! Any thoughts? Suggestions? Surely someone has the answer here! I appreciate any help/advice someone can give as this is driving me crazy! This is the last computer I need set up with pcAnywhere.

---

### Post by Mark Phelps on 2009-07-01
Don't know what version of PCanywhere you're trying to run, but if it's version 12, it most probably will NOT work.  The link below is to the CodeWeavers application compatibility page for PCAnywhere running in Wine or Crossover: 

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=917]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=917")

As you can see, v12 is rated Garbage.

---

### Post by mayallma on 2009-07-02
Hi Mark,

Thanks for the reply. The version is 12.5. It is supposed to be 'cross platform'. Since you sent me the link at WineHQ, does this mean it is actually emulating in a windows environment? Kind of weird since Symantec claims it will run on Windows, Mac, and Linux. Also weird that I can run the client software fine, just not the host. Any suggestions or comments would be greatly appreciated. Thanks!

---

### Post by philcamlin on 2009-07-02
yes wine emulates the windows environment to run windows apps

---

### Post by burebista on 2010-10-04
try this:
1. install j2sdk1.4.2_18 in /usr/lib/jvm/j2sdk1.4.2_18
2. run from console:
$sudo -s
$/usr/lib/jvm/j2sdk1.4.2_18/jre/bin/java -jar SetupLinuxMac.jar
and use the gui installer, it works 100%.
3. run from console
$sudo gedit /usr/bin/pcAnywhere
4. replace this line:
java -Djava.CPR.dirs=$PCAPATH -jar /usr/local/lib/pcAnywhere/vprcd.jar
with
/usr/lib/jvm/j2sdk1.4.2_18/jre/bin/java -Djava.CPR.dirs=$PCAPATH -jar /usr/local/lib/pcAnywhere/vprcd.jar
5. save the file /usr/bin/pcAnywhere
6. run from Alt-F2 or from Terminal "pcAnywhere".

That's it.

---

