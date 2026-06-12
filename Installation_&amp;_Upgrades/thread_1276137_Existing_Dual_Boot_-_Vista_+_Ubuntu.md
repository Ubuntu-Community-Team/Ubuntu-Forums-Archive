---
title: "Existing Dual Boot - Vista + Ubuntu"
date: 2009-09-26
forum: Installation &amp; Upgrades
---

### Post by therocco2k on 2009-09-26
Hello all,
I have a question I'm not sure can be done

I have an preexisting Dual Boot System with Windows Vista and Ubuntu Jaunty on 2 Seperate Partitions. Vista was the first installed, then Ubuntu. Since I spend all my Programing time on Linux and all my Movie Editing and Game Playing on Windows - I need a quicker way to move back and forth between the two OS's. I've decided there is a more efficient way to do this then rebooting each time I want to switch to a different OS for a different job I have to do, however I'm not sure how to go about making it work.

 Is there a way to MOVE or transfer my current Ubuntu Partition to a Virtualbox Session accesable through Windows Vista without creating a fresh install or new Virtual Installation/Machine. Reason Be, I have ALOT of customization and data on my Ubuntu OS and I cannot afford to do a clean install.

Is there any way to take my Current Ubuntu Install (separate partition then windows) and some how access it via Virtualbox or some other program in my current Windows Vista Installation without losing my Current Ubuntu Configuration or Install (Files, Customizations, Themes, Etc..)

If not thats ok, but there has to be a way!

Thank you, if you need more information about what I'm trying to accomplish let me know and I'll provide it to you. I Really need to get this working.

Thanks for your time, Knowledge - It's people like you in this forum that make the Open Source Community what it is today! Thank you so much

Rocco Castoro

**My Weekly Signature Quiz for Programmers:**

[COLOR=Navy]_If you were to Concatenate two variables, What are you doing to the variables?_[/COLOR]
*(HINT - You ate it in pre-school)*
If you're stumped, Private Message me for the answer. - Enjoy

---

### Post by yeats on 2009-09-26
> Is there a way to MOVE or transfer my current Ubuntu Partition to a Virtualbox Session accesable through Windows Vista without creating a fresh install or new Virtual Installation/Machine. Reason Be, I have ALOT of customization and data on my Ubuntu OS and I cannot afford to do a clean install.

Not really... Your Ubuntu setup is tied to the environment where it is installed.  You wouldn't be able to move it bit-by-bit to a VirtualBox HD and expect it to work.  

> Is there any way to take my Current Ubuntu Install (separate partition then windows) and some how access it via Virtualbox or some other program in my current Windows Vista Installation without losing my Current Ubuntu Configuration or Install (Files, Customizations, Themes, Etc..)


I've read that some people have done this, but it's bound to be a time commitment getting everything to work as expected and is probably not best practice :-).  Since your goal is to save time...

You might just figure out what it is about your customization that you would want to keep (/etc config files, dpkg -l results) and try recreating it piece by piece in a fresh VirtualBox install.  Either that or invest in a second computer to host either Vista or Ubuntu.

---

### Post by presence1960 on 2009-09-26
Vista takes a while to boot, but jaunty is pretty quick getting to the desktop. For myself only I never understood that " reboot takes too long" statement. Come on after all even if Vista takes a minute, how long is a minute? If you are in that much of a rush or pressed for time maybe you need 2 machines!

---

### Post by therocco2k on 2009-09-27
> **chrissharp123 said:**
> 
You might just figure out what it is about your customization that you would want to keep (/etc config files, dpkg -l results) and try recreating it piece by piece in a fresh VirtualBox install.  Either that or invest in a second computer to host either Vista or Ubuntu.

Well, there are so many different reasons why I run Ubuntu, I couldn't possibly replicate what I need in Windows - I like the Customization, the Programs, for instance; Even gedit is 10x more intellegent then Notepad or Wordpad - This is where I Code, and if you can imagine, if I prefer gedit over any windows text / editor then imagine the other features of linux I just cannot use Windows for.

Only if Ubuntu or Linux in general could utlize Video Card and Video Performance like Windows then I would Delete Vista and Throw away the CD. Can I get a Amen.... Wine is a joke, Still after all these years of development. Using Virtualbox in Linux to replicate Windows is one option, but the functionality you get out of using Virtualbox to run an OS like Windows just isn't useable for what I need graphically and Hardware wise. - 

I CANNOT EVEN USE MY NETGEAR WN111v2 Wireless USB Adapter with Ubuntu so I cannot access internet via Ubuntu. 

So I Guess I'll just switch back and forth between environments to work and play... What a bummer.

Thanks anyways guys.

BTW - System.out.print("UbutuForums.org equals.(Greatness)" );

---

### Post by dBuster on 2009-10-24
I am looking to do something similar, I am wanting to boot to Ubuntu and then be able to run Vista (it was pre-installed on this machine) in a Virtualbox.  All my troubles though are telling me about hardware settings and if I do this either I need to install vista again or risk not being able to boot just into Vista.  Still searching the forums though.  

As far as your wireless not working in Ubuntu, have you scoured the wireless forums for help?  I find it hard to believe that there is a wireless device not supported.

---

