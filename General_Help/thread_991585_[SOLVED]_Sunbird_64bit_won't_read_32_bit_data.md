---
title: "[SOLVED] Sunbird 64bit won't read 32 bit data"
date: 2008-11-23
forum: General Help
---

### Post by BobLand on 2008-11-23
I just installed 8.10 64 bit.  Got most things working OK but cannot get 32 bit Sunbird across.  There is very little on the web regarding this problem.  I have 3 years worth of data in there and I don't want to loose it.

Is there a way to get the 32 bit version of Sunbird so I can at least try to export the data out?

Kinda sucks that there is no facility to upgrade.  After spending an entire day getting things right because I had to reinstall the whole OS after the sound died and wouldn't come back, I am not looking forward to reinstalling 7.10 so I can export the data out then reinstall 8.10 and hope the data imports.

bobland

---

### Post by ju2wheels on 2008-11-24
You should be able to install it without a problem. I havent tried force installing something since I had to do it for a skype a while back, but it should work. Just use getlib to satisfy the dependencies of the 32bit Sunbird and then force the architecture on the install from the command line for Sunbird 32bit.

getlibs [ [http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790) ]

---

### Post by BobLand on 2008-11-24
Let me be more specific.  I'm able to install Sunbird but only the 64 bit version.  It will not read my 32 bit storage.sdb which contains 3 years worth of very necessary data.

Apparently, the new sunbird is using a new format for the database which is states is not compatiable with the older version.

I searched the mozilla projects/sunbird site but found no evidence of this error event.

I also tried getlibs.  It downloaded a variety of libs but did not change the situation.

Any help is appreciated.

bobland

---

### Post by ju2wheels on 2008-11-24
What I meant was that you can use getlibs to install the dependencies for the 32bit version of Sunbird, then install the 32bit version of Sunbird for the purposes of accessing and exporting your 32bit data. 

You can then, in theory, be able to upload that data to the 64bit version. So if you ran getlibs on the the 32bit version of Sunbird, now you have to specifically install the 32bit version and run that one to access your data instead of the 64bit version that gets installed by default.

Edit: Since your error seems to be version specific you will most likely have to grab the appropriate 32bit version as well from the debian repositories at debian.org.

---

### Post by BobLand on 2008-11-24
I ended up installing the 32 bit tar with help from a Debian web page.  Got everything back to normal.

What confuses me is installing tars.  I had tried this a few times but could not get the OS to recognize the binaries.  The web page instructed to move the untared directory -- sunbird, in this case, to /opt, create a link into /usr then create a sunbird.desktop file which inserted sunbird into Applications->Office.

After pointing the profile.ini to the desired defaults directory everything came back.

In the future, if I want to install a program from a tar, should I follow the outline as above or are there other tricks to know about?  Apparently, just untaring a file is not enough.

Thanks,
bobland

---

### Post by ju2wheels on 2008-11-24
Right in the end you did the same thing as forcing an install using a debian package except by compiling source code. The reason it failed the first time is because you were missing the 32bit dependencies which getlibs put in there for you.

Getlibs grabs all the 32bit libraries and programs needed by the 32bit program you want to install. On a 64bit system, only 64bit libraries will show up in Synaptic (for the most part), so it doesnt know where to get the 32bit versions from. Getlibs helps solve this problem.

You can find a little more info on packages/dependencies here: [https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

Tars are usually source code archives, and for the most part you will usually want to avoid it if possible and use packages from Synaptic, or .deb files to install programs. In the above case, yes placing it /opt was the safest thing to ensure you dont have any 32bit vs 64bit complications involving the installation locations. Also since you are using 64bit Ubuntu, in the future I would also recommend sticking to 64bit packages where ever possible.

---

