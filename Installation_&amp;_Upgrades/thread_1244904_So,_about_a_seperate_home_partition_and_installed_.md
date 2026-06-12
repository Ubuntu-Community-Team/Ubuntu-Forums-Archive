---
title: "So, about a seperate home partition and installed applications..."
date: 2009-08-20
forum: Installation &amp; Upgrades
---

### Post by billdotson on 2009-08-20
Forgive the misspelling of "separate" in the title but to the question now:

If someone has a separate home partition that all the programs are installed in when they reinstall a Linux OS and mount that as the home partition aren't some of those programs going to have issues running correctly? As I understand it there are libs and such in /usr/lib and other places that applications rely on to run properly. Wouldn't it be a huge pain to fix all that kind of stuff? Or, could you run a command to add and move around the correct libraries? I believe I have used ldconfig before to make sure all links between libraries were updated. This question is especially important as I have been having to install a lot of things form source lately.

Thanks.

---

### Post by running_rabbit07 on 2009-08-20
If you have the 3 partition setup like this, then up grading/reinstalling will be easier.

/ This partition contains all of you programs and OS files.(This partition is the only one affected during reinstallation, unless you click to format the /home.)

/home This partition contains all of your personal files such as music and documents. It also contains information files that programs use such as Firefox Bookmarks and Email if you use Thunderbird or Evolution. It doesn't usually contain any actual programs, just settings.

SWAP  Stores nothing, it's just for temporary storage when your RAM is filling up and when you hibernate your system.

Does that help? If you want to know more, just ask.

---

### Post by zarthon on 2009-08-20
The /home partition stores user files and settings 
It is similar to C:\Documents and Settings\ in windows

Programs installed by root or with root permissions are installed for all users. Packages usually place program files and resources in /usr and /var, and global system settings files in /etc. 
This includes anything installed with the synaptic package manager.

User settings are stored in /home/username/ in a file starting with a . like .mozilla where all your firefox links, settings passwords and customizations are stored.

You can safely migrate all the data and most settings in /home to a new linux system. If you experience any problems with a particular application you would want to rename your settings for that file so that a new one is created. Settings files between program versions do not always work correctly.

If you are dual booting a few different versions of linux that all use the same /home partition the question of settings files gets more complex. Also data files created with new versions of applications installed on another system may not be usable in an older version. 

Programs installed by users without root permissions which might include downloaded tar balls. Are sometimes installed in a user's home directory. If you are using tar balls then the question about the libs is the case from the start. Without the package manager figuring out and installing dependencies for you then you will have to figure them out and install them on your own. For this and other reasons it is better to stay with the packages for your distribution and version.

---

### Post by zarthon on 2009-08-20
I had not read Ronnie's valuable and more concise post. 
To Bridge to what we said if you only have two mount points:
/
and 
/home 
then /usr /lib /var /etc and everything else are all on the file system mounted at /.  Everything but /home will be on the file system mounted at /.

Another thought
You want to have the separate /home also because it will keep users from binding up the system by accidentally using all the system storage space. All that will happen when /home is full is that users can not save more data until they delete something.  If / is full then the system will not function correctly.

---

