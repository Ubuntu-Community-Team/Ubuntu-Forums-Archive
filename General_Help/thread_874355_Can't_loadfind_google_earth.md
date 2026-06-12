---
title: "Can't load/find google earth"
date: 2008-07-29
forum: General Help
---

### Post by alliance1975 on 2008-07-29
Downloaded google earth .bin file to desktop. try double click = no work. Try hours of terminal commands and all i get is  not valid command. I can't even find out how to get to my desktop folder in terminal.  isn't there a manual on basic terminal commands somewhere? tried debian package from synaptic and now can't find package anywhere on computer. going crazy. just tell me google earth won't work on ubuntu and i'll give up.

---

### Post by phidia on 2008-07-29
Google Earth will work..take a deep breath...did you try just right clicking and the run option? If you installed the debian package it should appear in your menu or press the Alt + F2 keys and start to enter the package name.
And many guides for system commands and admin are [here]("https://help.ubuntu.com/community/SystemAdministration").

---

### Post by oldos2er on 2008-07-30
Open a terminal, type "cd Desktop" to change to your desktop directory (Linux is case-sensitive). First type "chmod a+x GoogleEarthLinux.bin," then "sudo ./GoogleEarthLinux.bin".

---

### Post by brujoand on 2008-07-30
>  "sudo ./GoogleEarthLinux.bin".

You shold _NOT_ do this, You should almost never run programs with sudo, except when your installing something or doing network stuff like tcpdump where you have to run as superuser. 
And anyway, the reason you did the chmod, was so you did not have to run Googleearth as superuser.

---

### Post by finite9 on 2008-07-30
why are you using the bin file?  google earth is in the repositories!

search for it in synaptic or do sudo apt-get install <googlearth>  (cannot remember exact name of package, sorry)

---

### Post by drs305 on 2008-07-30
Enable the medibuntu repository and install it through synaptic:

For Hardy:

Install Medibuntu Repository (from [https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")): 

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

```

Install Google Earth (this is a metapackage, no version number required. current version 4.3):
```
sudo apt-get install googleearth
```

---

### Post by oldos2er on 2008-07-30
> **GrimmVarg said:**
> You shold _NOT_ do this, You should almost never run programs with sudo, except when your installing something or doing network stuff like tcpdump where you have to run as superuser. 
And anyway, the reason you did the chmod, was so you did not have to run Googleearth as superuser.

 Running Googleearth with sudo installs it in /opt, where it is available systemwide for all users. Note you say "except when your [sic] installing something".

---

### Post by oldos2er on 2008-07-30
> **finite9 said:**
> why are you using the bin file?  google earth is in the repositories!
  

 The *.bin file from Google is more up-to-date than the version in the repositories.

---

### Post by finite9 on 2008-07-30
> **oldos2er said:**
> The *.bin file from Google is more up-to-date than the version in the repositories.

yeah, the eternal question: should I really install that unsigned application that will never get security updates?

No matter how recent and cutting edge ubuntu is with merges from debian unstable, it is *never* up-to-date with latest releases of packages.  I tend to try my best to stick with repository packages, unless there is something that I absolutely must have that is in a tar.gz/bin file or whatever.  It is a long time since I had to search for custom DEBs or compile by hand to get 'basic' apps working in Linux.

Newer release may contain newer functions but is not that often that those functions are must haves for me and im willing to wait six months in those cases.  For some people though, maybe it really is a must have.

---

### Post by alliance1975 on 2008-07-30
medibuntu loaded ok. almost got googleearth but got hung at the googleearth eula screen, (no matter what i did i could'nt get past the <ok>. rebooted, went to synaptic and got this:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

---

### Post by maughansterman on 2008-07-30
restart computer and delete all cookies

---

### Post by drs305 on 2008-07-30
```
sudo dpkg --configure -a
```

Were you able to highlight the OK and start the install? You get to the OK with tab, if I remember correctly, on a lot of these EULA pages.

---

### Post by SunnyRabbiera on 2008-07-30
> **oldos2er said:**
> The *.bin file from Google is more up-to-date than the version in the repositories.

yes but its not a guarentee, latest doesnt always mean "greatest"

---

### Post by alliance1975 on 2008-07-30
first thanks to all who replied with help. finally got google loaded. at the eula window i just started hitting f keys until f12 got me to a window that allowed me to answer the eula and move on. Launched google earth with alt-f2 and the screen did nothing but flicker and flash. went back to synaptic and removed google earth. did file search and nothing googleearth showed up. i assume i got rid of all.

trying to do what i thought was a simple task, (load an application), turned out to be quite humbling. ultimately the result was terrible. i will keep ubuntu on my laptop for a hobby but as much as i hate to say it my small home network will continue to rely on windows.

---

### Post by brujoand on 2008-07-31
yeah, my bad. I thought it was the old bin, wich i was the actual google eart  OOooops :P

---

### Post by mcmilner on 2008-07-31
> **oldos2er said:**
> Open a terminal, type "cd Desktop" to change to your desktop directory (Linux is case-sensitive). First type "chmod a+x GoogleEarthLinux.bin," then "sudo ./GoogleEarthLinux.bin".

Thank you, Ann. :KS  I was grateful to find this straightforward answer, after messing around for an hour.

I love Linux.  I've dumped windows, but even as an experienced PC user and former big machine programmer, there are too many things about Linux that are too nerdy for everyday users and the manuals I have all have the attitude that you must understand how life formed on earth in order to know how to make babies.

So, does your 3-step procedure applies to all .bin files that I download?  Maybe I can start downloading. 

Margot

---

### Post by oldos2er on 2008-07-31
> **mcmilner said:**
> Thank you, Ann. :KS  I was grateful to find this straightforward answer, after messing around for an hour.

I love Linux.  I've dumped windows, but even as an experienced PC user and former big machine programmer, there are too many things about Linux that are too nerdy for everyday users and the manuals I have all have the attitude that you must understand how life formed on earth in order to know how to make babies.

So, does your 3-step procedure applies to all .bin files that I download?  Maybe I can start downloading. 

Margot

Yes, you can use that formula for any *.bin file. It's always best to use Ubuntu's repositories--at least check them first to see if the program you want is available there.

 You might want to read [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by Jerry41 on 2008-08-02
> **drs305 said:**
> Enable the medibuntu repository and install it through synaptic:
  .  .  .  

I followed your instructions (with the exception of one apparent typo) and had Google Earth up & running in about 15 minutes. It looks like it runs smoother than it ever did in XP, & it doesn't bog the pc down like it did in XP. 

Thanks again

---

### Post by drs305 on 2008-08-02
> **Jerry41 said:**
> I followed your instructions (with the exception of one apparent typo) and had Google Earth up & running in about 15 minutes. It looks like it runs smoother than it ever did in XP, & it doesn't bog the pc down like it did in XP. 

Thanks again

I hate typos! Gone back and fixed. Thanks.

---

