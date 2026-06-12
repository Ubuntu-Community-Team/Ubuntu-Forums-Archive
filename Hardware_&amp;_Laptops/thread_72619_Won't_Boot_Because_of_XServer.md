---
title: "Won't Boot Because of XServer?"
date: 2005-10-06
forum: Hardware &amp; Laptops
---

### Post by bugmenot on 2005-10-06
Hi, I'm very new to Linux so please bear with me.
Today I tried installing Ubuntu, everything went smooth untill it almost boot to the desktop. It said Xserver (or XOrg) couldn't start because my display driver. I read a review of Ubuntu he had the same problem, he said to fix it sudo dpkg-reconfigure xserver-org 
Now I tried that but I think it's trying to only work on my onboard card which of course, no one wants to use and I would like to know how to switch to my ATI 9200, becaseu I think that would fix it

---

### Post by ltmon on 2005-10-06
Hi,

You could try installing the ATI binary graphics drivers: 

[https://wiki.ubuntu.com/BinaryDriverHowto/ATI](https://wiki.ubuntu.com/BinaryDriverHowto/ATI)

L.

---

### Post by landotter on 2005-10-06
Disable the on-board card in the bios if possible.

---

### Post by bugmenot on 2005-10-06
I'll try that guide, thanks, and I already disabled the onboard video.

---

### Post by bugmenot on 2005-10-06
Doesn't work :( What it says in the log is something like this
libglcore..blahblah no symbols (says that a lot of times)
No matching device section (busid pci:2:10:0) found

---

### Post by bugmenot on 2005-10-06
PLEASE HELP! I'm dying to get started

---

### Post by landotter on 2005-10-06
Log into IRC, it'll be more active than the boards right now: #ubuntu/irc.freenode.net

good luck!

---

### Post by mlomker on 2005-10-06
> No matching device section (busid pci:2:10:0) found

I'm not sure about the on-board video deal, but my [how-to]("http://www.ubuntuforums.org/showthread.php?p=348911") will definitely get the drivers installed for you.

---

### Post by bugmenot on 2005-10-06
Your guide explains how to set it up in the actuall graphical GUI state, which I can't even enter

---

### Post by bugmenot on 2005-10-06
Yes, I got it working. I left BusID blank. But now I can't login? During the install it asked me for my name.. Is that the login? Because that doesn't work

---

### Post by mlomker on 2005-10-07
> Is that the login? Because that doesn't work

It asks for your name and the login.  For me the login is mlomker and my name is Michael Lomker...I'm not sure what you put in.  If you go back to the command line you can always **cat /etc/passwd** to see what you had entered.

My ATI how-to can be done entirely from the command-line by using 'nano' as the editor.

---

### Post by bugmenot on 2005-10-07
:D works great! Thanks a bunch guys! But now I have a few last questions;) Here, in Ubuntu, it seems the most refresh rate I can go is 75 while in Windows it's 85, and it's the same res. Also, what's the command to run the cog wheels? fglrx or something close?

---

### Post by mlomker on 2005-10-07
> Here, in Ubuntu, it seems the most refresh rate I can go is 75 while in Windows it's 85, and it's the same res.

Yeah, Ubuntu uses the 'recommended' refresh rate that the monitor sends to the driver even if that isn't the highest one.  That's something that the monitor manufacturer programs in.  There is a way to over-ride it by using a **modeline** but it's a real hassle.

> Also, what's the command to run the cog wheels? fglrx or something close?

Take a look at the *testing if it works* section of my [how-to]("http://www.ubuntuforums.org/showthread.php?p=348911").

---

### Post by bugmenot on 2005-10-07
Ahhhhhhh! I did that guide and after I got rid of all the fglrx stuff, and tried installing the .deb packages, it said that it couldn't create the 1.2.so or something folder, so i restarted, ta da! Xserver wouldn't boot up. So I do dpkg-reconfigure xserver-xorg and it said it couldn't open because either they were broken or missing... gah! How do I fix this?

---

### Post by mlomker on 2005-10-07
> Ahhhhhhh! I did that guide and after I got rid of all the fglrx stuff, and tried installing the .deb packages, it said that it couldn't create the 1.2.so

Yeah, you aren't the first person that has happened to.  I'm not sure what causes that.

Try:

```

sudo apt-get install --reinstall xlibmesa-gl

```

---

### Post by bugmenot on 2005-10-07
=/ it said it coulnd't find xlibmesa-gl

---

### Post by mlomker on 2005-10-07
[QUOTE=bugmenot]=/ it said it coulnd't find xlibmesa-gl[/QUOTE]

Then there's something wrong with your Internet connection or your repository configuration.

You can either download the package from [http://packages.ubuntu.com](http://packages.ubuntu.com) or off of the installation CD and get it onto your machine somehow, or I could try emailing you that one file I suppose.  You'd have to give me an email address for that...and then you'll have to get that file into the correct directory using a floppy or some other means.

If you get the .deb package from the above site then it'd be installed like this:

```

sudo dpkg -i packagename.deb

```

---

### Post by bugmenot on 2005-10-07
My internet works just fine =/ that's how I'm writing this. And I would have no use in downloading it because how would I go about installing it? I don't even have a floppy anyway. Ugh I shouldn't of done that guide :(

---

### Post by mlomker on 2005-10-07
> That's how I'm writing this. 

I thought you said that you couldn't get to your desktop?

> And I would have no use in downloading it because how 
would I go about installing it? I don't even have a floppy anyway.

I provided you with the dpkg command for installing it in the last post.

I clearly state at the beginning of the guide that people should use the included driver if it works for them and you had stated in a previous post that it was working for you.  I'm still not sure why you decided to upgrade.

---

### Post by bugmenot on 2005-10-07
[QUOTE=mlomker]I thought you said that you couldn't get to your desktop?
I'm using dual boot. I'm on Windows right now


I provided you with the dpkg command for installing it in the last post.

I clearly state at the beginning of the guide that people should use the included driver if it works for them and you had stated in a previous post that it was working for you.  I'm still not sure why you decided to upgrade.[/QUOTE]
I installed the ATi drivers but when I fglrxinfo (or something close) it said it was mesa, that's why I tried uninstalling everything and reinstalling, and then it didn't work. When you say you rpiveded the dpkg command do you mean the sudo apt-get -install --reinstall xlibmesa-gl? that doesn't work like I said, it says it cannot be found. If you mean you provided the link, I replied saying I have no use for it because how can I download/install it from safe boot?

---

### Post by mlomker on 2005-10-07
> I replied saying I have no use for it because how can I download/install it from safe boot?

Then you must be dual-booting into Windows or something because you told me that 'your Internet is fine'.  

The dpkg command is what would install the .deb once you got it onto the machine.  If you don't have a CD burner, a USB drive, a shared VFAT partition, or any other way to get the file then I guess you'll have to reinstall Ubuntu.  

I'm not sure what to suggest because I don't know what you have.

---

### Post by bugmenot on 2005-10-07
My internet works in Windows. I typed that command in Ubuntu's recovery mode where you only have the ms-dos like console and it said it couldn't find the package. Could you please make sure that's the correct spelling?

---

### Post by mlomker on 2005-10-07
> Could you please make sure that's the correct spelling?

It is.  You can search for package names using this command:

```

apt-cache search *packagename*

```

In this case you could search on mesa.

---

