---
title: "WD Passport  Issue - I am a complete beginner!!!"
date: 2011-05-02
forum: Hardware
---

### Post by ganesh3 on 2011-05-02
Hi,

Firstly, I would like to say that I am happy that I moved from Windows to Ubuntu but now I am facing issues that any new beginner faces when he/she changes an OS. 

I would like to inform that I am complete beginner and have no clue to resolve the issue I am facing.

I had Windows 7 installed on my Laptop and decided to switch to Ubuntu 11.04 64-bit OS.

Before switching, I took back up of all my data in WD Passport External Hard disk which is 500 GB in size.

But after installing Ubuntu, I tried to restore my data and to my surprise I couldnt do it because WD has Password Protect feature which needs to run unlock.exe. I tried to run it using Wine but it gave an error and could not run it. So now I cant access my data as I cannot unlock my drive.

So I decided to search the forum and looked up issues similar to mine. I did find some but all said that eventually I will have to copy the data somewhere my accessing it through Windows and then format the WD hard drive.

I have 500 GB of data in it and to copy it to some location, then formating and putting data back into it is like a punishment to me for moving from one OS to another.

It would be great if there is a way to access this unlock.exe and access my data through Ubuntu.

Awaiting replies. I can provide any information that you need.

Thanks,

Ganesh.

---

### Post by barthus on 2011-05-02
> **ganesh3 said:**
> But after installing Ubuntu, I tried to restore my data and to my surprise I couldnt do it because WD has Password Protect feature which needs to run unlock.exe. I tried to run it using Wine but it gave an error and could not run it. So now I cant access my data as I cannot unlock my drive.Ganesh.

Did you password-protect the disk before under Windows?

---

### Post by ganesh3 on 2011-05-02
> **barthus said:**
> Did you password-protect the disk before under Windows?

Yes I did. Can I execute a command through the terminal to execute the exe by providing the argument as password to open the WD hard drive?

Let me know.


Thanks,

Ganesh Bhat

---

### Post by Jouke74 on 2011-05-02
Another option is to make (or download) a temporary virtual machine with Virtualbox or VMware. Not the easiest way, but this should work.

---

### Post by ganesh3 on 2011-05-02
> **Jouke74 said:**
> Another option is to make (or download) a temporary virtual machine with Virtualbox or VMware. Not the easiest way, but this should work.

So what you are suggesting is that I download one of these and run windows on them to access my files. Am I right?

Do I need a Windows 7 iso file for it or the exe through a CD is fine?

Please let me know.

Thanks,

Ganesh Bhat.

---

### Post by barthus on 2011-05-02
> **ganesh3]Yes I did. Can I execute a command through the terminal to execute the  exe by providing the argument as password to open the WD hard drive?[/QUOTE]

I think you have to pass this barrier: Go back to Windows and de-activate/delete your passwd and/or update your data onto another disk ... before you start to try out many 'possible' actions which take a long time and might be even dangerous for your data.

[QUOTE=Jouke74 said:**
> Another option is to make (or download) a temporary virtual machine with Virtualbox or VMware. Not the easiest way, but this should work.

Yep, that could be one solution. Or: Search a second PC with Windows on it.

---

### Post by barthus on 2011-05-02
> **ganesh3 said:**
> So what you are suggesting is that I download one of these and run windows on them to access my files. Am I right?

Do I need a Windows 7 iso file for it or the exe through a CD is fine?

If you decide to use a virtual box you need to install it. Like:

```

sudo apt-get install virtualbox-ose virtualbox-ose-guest-utils virtualbox-ose-dkms
 
```Then start virtual box, configure your system and boot with your Windows 7 CD. More details can be found here: [http://www.virtualbox.org/](http://www.virtualbox.org/)

---

### Post by ganesh3 on 2011-05-02
> **barthus said:**
> I think you have to pass this barrier: Go back to Windows and de-activate/delete your passwd and/or update your data onto another disk ... before you start to try out many 'possible' actions which take a long time and might be even dangerous for your data.



Yep, that could be one solution. Or: Search a second PC with Windows on it.

Thanks for all your suggestions and advise.

I just unprotected my hard drive my removing the security settings for the hard drive by accessing it over a windows machine and now it opens the hard drive wit my data.


Thanks,

Ganesh Bhat

---

