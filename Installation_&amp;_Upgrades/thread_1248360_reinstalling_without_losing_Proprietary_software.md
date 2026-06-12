---
title: "reinstalling without losing Proprietary software"
date: 2009-08-24
forum: Installation &amp; Upgrades
---

### Post by yairsuari on 2009-08-24
Hi and thanks for the help
I am using kubuntu 8.04 with some Proprietary software installed (vmware player, matlab, compilers) and i have somehow managed to screw up my system (for 2 weeks now i am trying to fix sound card, then kde upload then wifi driver and who knows what next)
is there a way to reinstall the system from start without losing any installed software?
i have seen some threads dealing with reproducing your currently installed packages and will use them but were not able to find anything about this.
thanks again
yair

---

### Post by stlsaint on 2009-08-24
yes you can do what you ask...its called backups...
and you can also save all programs you have installed thru repos as well...in repos go to file and "save markings as..." this will create a document that synap can read to re-install all marked programs you have!! 
i recommend you use the simple backup config suite/tool to make a backup of /home,/etc/var/...and so on so once you re-install you will have all you need...and other software that you installed thru wine...you can back that up to...just do a full backup of your system prior to re-install!!

---

### Post by Mark Phelps on 2009-08-25
> **yairsuari said:**
> ... is there a way to reinstall the system from start without losing any installed software?
Sorry, no.
> i have seen some threads dealing with reproducing your currently installed packages and will use them but were not able to find anything about this.
That's called AptOnCD and will allow you to create a record of all the packages you have installed so you know what to reinstall.

---

### Post by stlsaint on 2009-08-25
> **Mark Phelps said:**
> Sorry, no.

That's called AptOnCD and will allow you to create a record of all the packages you have installed so you know what to reinstall.


maybe im missing something here...i may be wrong and just need clarification...i have just used simple backup config tool  to backup my system so im wondering what Mr. Phelps means by no you cant back up programs installed...like i said not here to start confrontation...if im wrong please correct me as i dont want to give false info. But things may be different with kubuntu 8.04 as im not familiar with it...and i am able to save my installed programs to a document thru synap manager of all installed programs...so im under the impression that either im wrong or Mr. Phelps is wrong...please give more understanding so we can help this poor lad out here!! BTW im using jaunty with alot of extras!!

---

### Post by presence1960 on 2009-08-25
when doing a reinstall or upgrade all programs installed manually (not thru synaptic or apt-get will be lost or non functional). I don't think backing the programs up will work because unlike windows components of any software package are located in more than one directory. So you would have to manually reinstall those programs again for them to work. That is unless you backed up each part of the program from each directory that contains them such as /home -> config file, /usr/bin -> executable , etc

For clean install there are a number of ways to save your programs- but again only those installed thru synaptic or apt-get

---

### Post by stlsaint on 2009-08-25
> **presence1960 said:**
> when doing a reinstall or upgrade all programs installed manually (not thru synaptic or apt-get will be lost or non functional). I don't think backing the programs up will work because unlike windows components of any software package are located in more than one directory. So you would have to manually reinstall those programs again for them to work. That is unless you backed up each part of the program from each directory that contains them such as /home -> config file, /usr/bin -> executable , etc

For clean install there are a number of ways to save your programs- but again only those installed thru synaptic or apt-get


thank you...that is what i meant by saying backup programs...thru synap! but i also thought that if you made a backup of your entire system than you could also take the programs installed thru wine or manualy...ie executable file! maybe my words and Mr. phelps understanding of what i meant got crossed as he posted that you could not backup programs! Thanks to all posters overall...

---

### Post by Mark Phelps on 2009-08-25
> **stlsaint said:**
> maybe im missing something here...i may be wrong and just need clarification...i have just used simple backup config tool  to backup my system so im wondering what Mr. Phelps means by no you cant back up programs installed

Folks come here all the time with "I just upgraded to x.xx and now nothing works! How to I get back to y.zz?" So, when the OP asked if there was a way to reinstall without losing stuff, I interpreted that to mean some kind of "rollback" capability (like System Restore in MS Windows) which, as you probably know better than me, there is not.  

Where did I say "no you can't backup programs installed"?? Was it where I mentioned using AptOnCD? Of course, if you do backups, you can get stuff back.  I do that myself all the time!

Please don't put words into my mouth.

---

### Post by stlsaint on 2009-08-27
> **Mark Phelps said:**
> Folks come here all the time with "I just upgraded to x.xx and now nothing works! How to I get back to y.zz?" So, when the OP asked if there was a way to reinstall without losing stuff, I interpreted that to mean some kind of "rollback" capability (like System Restore in MS Windows) which, as you probably know better than me, there is not.  

Where did I say "no you can't backup programs installed"?? Was it where I mentioned using AptOnCD? Of course, if you do backups, you can get stuff back.  I do that myself all the time!

Please don't put words into my mouth.


Sir, Mark is it...can i call you Mark...:)
Please forgive my misundertanding...as you can see in the EDIT that i posted prior to you posting that i didnt quite catch what you were responding to till after i had already responding..once i realized that he aske could he re-install without losing his programs as in they be there once he re-boots after install than i corrected my self and added a edit to my post saying that it was my fault. Once again sorry for the mishap!!

---

### Post by Mark Phelps on 2009-08-27
> **stlsaint said:**
> Sir, Mark is it...can i call you Mark...:)
Sure ... anytime. We're not formal around here :)

> Once again sorry for the mishap!!
OK, thanks.

But on another note, perhaps your and/or Presence could respond with a concern I have about the OP's original question?  I keep hearing that if you create a separate /home partition, when you reinstall Ubuntu, or even if you upgrade to a new Ubuntu version, it will keep "everything".  

I find that hard to accept.  Let me tell you why.

I have a highly-customized system with stuff I created/modified all over the place:  /boot, /etc, /dev, /usr, run-level init files ... and so forth. So while I understand that the stuff under /home gets preserved, what about all this other stuff? Does that get preserved (as in NOT overwritten) as well?  In other words, if I've added module lines to my file (forget which one), will the reinstall/upgrade detect that and leave the file alone?

---

### Post by presence1960 on 2009-08-27
> **Mark Phelps said:**
> Sure ... anytime. We're not formal around here :)


OK, thanks.

But on another note, perhaps your and/or Presence could respond with a concern I have about the OP's original question?  I keep hearing that if you create a separate /home partition, when you reinstall Ubuntu, or even if you upgrade to a new Ubuntu version, it will keep "everything".  

I find that hard to accept.  Let me tell you why.

I have a highly-customized system with stuff I created/modified all over the place:  /boot, /etc, /dev, /usr, run-level init files ... and so forth. So while I understand that the stuff under /home gets preserved, what about all this other stuff? Does that get preserved (as in NOT overwritten) as well?  In other words, if I've added module lines to my file (forget which one), will the reinstall/upgrade detect that and leave the file alone?

A separate home partition has the advantage that a lot (not all) config files are kept there. So after a clean install once you reinstall or do [this]("http://ubuntuforums.org/showpost.php?p=7157175&postcount=5") as I do all your settings for those programs are there(i.e. firefox, gkrellm, grsync etc) All those other customizations that are outside the /home partition are lost. That link only works for software installed from Synaptic or apt-get CLI. As I mentioned earlier all manual installations are lost or rendered inoperable if not uninstalled prior to a new install/upgrade and maually reinstalled after.

Good concern Mark and all those customizations you have would have to be redone on a clean install unless you keep the current partition scheme and do a manual install and designate the mount point of each directory.

---

### Post by Mark Phelps on 2009-08-27
> **presence1960 said:**
> Good concern Mark and all those customizations you have would have to be redone on a clean install unless you keep the current partition scheme and do a manual install and designate the mount point of each directory.

OK ... guess I didn't phrase my question well.

If I do a reinstall or upgrade and reuse the same partitions as are presently there (assuming the installer lets me do that without reformatting them), will my modified files be left intact, or will the installer replace them with older versions (reinstall) or with newer versions (upgrade).

Please note that I'm not actually planning on doing this, I'm just curious as to what would actually happen.

---

### Post by stlsaint on 2009-08-27
well i would think that an upgrade would not hinder your folders altho thru the forums im sure you have seen all the issues that come with upgrading so i wouldnt recommend it to anyone...but as far as a re-install that seems to be that unless you make a full system backup and then re-install the same OS you just had...then replaced all the new dir with your old ones manually using the restore tool than that would be the only way to keep your customs...so to throw my two cents in...No i dont thing there is a way to re-install/upgrade and keep everything the same without some extra work afterwards...hope i helped some!!

---

### Post by presence1960 on 2009-08-27
A clean install will allow you to use your present partitioning scheme as long as you use the manual option. highlight each directory (partition), click edit and set the filesystem & mount point- **_just be sure to leave the format box unticked_** and all data will remain undistubed.

example: if /usr is sda3 then highlight the sda3 partition & click edit. Then set the parameters (filesystem & mountpoint /usr) leaving format unticked. That's exactly how you set up an existing separate home partition.

---

### Post by Mark Phelps on 2009-08-28
OK ... so if I understand what you're both saying, even if I reuse the same partitions for a reinstall, all the files and folders in those partitions will get overwritten when the reinstall is done.

So, basically, when folks are saying that having a separate /home partition will allow you to "downgrade" (as in, reinstall using a lower-version of Ubuntu) without losing "anything", that is not correct. Right?

I'm asking because I keep seeing threads where former MS Windows folks keep asking about the Linux equivalent of MS System Restore (even though, since they're asking that, they REALLY don't know how System Restore works!) and the reply they're given most often is to have a separate /home partiton so they can reinstall an older version of Ubuntu and not lose "anything".

I've suspected that this is really not true, but I've not actually tried it and wanted to hear from others more expert than me on this.

Thanks for your feedback, guys,

---

### Post by presence1960 on 2009-08-28
> **Mark Phelps said:**
> OK ... so if I understand what you're both saying, even if I reuse the same partitions for a reinstall, all the files and folders in those partitions will get overwritten when the reinstall is done.

Mark in your case you can keep those partitions and all their data by choosing a manual install. I know you said you have separate /boot, /usr & /etc partitions. You can still use them & retain all data on them as well by choosing a manual install. Then highlight each partition, click edit and set parameters such as filesystem & mount point. Just be sure to leave the format box unticked for obvious reasons. Choose the partition to install / onto and proceed with the install.

As far as a system restore type capability it does not exist. I create a file with all my installed packages and after reinstall I place that file in my home and run a command and it downloads & installs all my software from my previous install except for those manually installed. I have the link for that procedure in a previous post on this thread.

---

