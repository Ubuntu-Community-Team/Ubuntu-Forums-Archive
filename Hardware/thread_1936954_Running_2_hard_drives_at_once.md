---
title: "Running 2 hard drives at once"
date: 2012-03-06
forum: Hardware
---

### Post by batophobia on 2012-03-06
So I am in a class where we are learning Linux (using Ubuntu 11.10).  Long story short, I had to put the hard drive from the school PC into my personal computer.  Therefore, I have my personal HDD (Windows 7) and the school HDD (Ubuntu) in my one desktop.  Now that you are caught up I have a question.

Is it possible for me to have my Ubuntu HDD running while I am running my computer off of my Windows HDD?  For my class, I need to be able to have the machine working similar to a server (having apache and what-not), plus the professor wants to grade everything through SSH, so in order for it anything be graded I have to keep my Linux HDD running.  I honestly have no clue where I would even start looking for a solution for this so I am hoping this forum can at least point me in the right direction.

My computer specs (Links are newegg pages for each part):
[Processor]("http://www.newegg.com/Product/Product.aspx?Item=N82E16819103851"): AMD Phenom II X6 1055T Thuban 2.8GHz Socket AM3 125W
[Motherboard]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813131366"): ASUS M4A78T-E AM3 AMD 790GX HDMI ATX AMD Motherboard
[RAM]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820145224"): 6GB DDR3
[Power]("http://www.newegg.com/Product/Product.aspx?Item=N82E16817152035"): RAIDMAX HYBRID 2 RX-630SS 630W ATX12V V2.2/ EPS12V
[Graphics]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814102865"): SAPPHIRE Vapor-X 100284VXL Radeon HD 5750 1GB 128-bit GDDR5
[HDD]("http://www.newegg.com/Product/Product.aspx?Item=N82E16822136533"): 1TB Western Digital (Windows 7)
HDD: 80GB Seagate? [I'd have to look] (Ubuntu)

---

### Post by alenis on 2012-03-07
You can probably solve the problem running Ubuntu as a Virtual Machine, e.g. using Virtual Box.

---

### Post by batophobia on 2012-03-07
How in depth does virtual box go?  Part of the class is installing WINE and running windows applications through Ubuntu.  I realize it is kind of redundant to go through Ubuntu to get back to windows but I have to be able to do that.

Also, is it possible to run virtual box using a 2nd hard drive?  I haven't messed with it at all so I am just asking questions for curiosity's sake.

---

### Post by alhera on 2012-03-07
To fix this kind of problem you have a good option. You can use ubuntu system for this. Hopefully it would be helpful for you.

---

### Post by Grenage on 2012-03-07
As covered above, virtualisation is about your only option.  You should be able to use wine within VB without issue.

---

### Post by Mark Phelps on 2012-03-09
Folks here bring up the VirtualBox solution like it's a simple and miracle cure -- which it's NOT.  You mentioned "school PC" which has Win7 on it.  Is this your own PC which you use for school?  Did the PC come with Win7 preloaded?

Asking these questions because VirtualBox requires a complete REINSTALLATION of the OS you want to use, in this case, Win7.

If the "school PC" came preloaded with Win7, then you can't LEGALLY either connect the hard drive to another PC, or reinstall that version of Win7 in another PC.  Preinstalled versions of Windows OSs are known as "OEM" and are licensed ONLY to the original PC on which there were installed.

Also, MS has gotten a lot better in recent years about detecting multiple uses of their OSs, so even if you do have your own  version of Win7, when you install it in your other PC using VB, when you go to activate it, it's most likely to detect that it's already been activated and refuse to allow you to activate it again.  But, if it is a Retail version, it might work anyway.

Also, any Windows apps you have installed on the HDD would also have to be completely reinstalled in the VB -- and many will face the same reactivation issue, especially if you're using MS Office.

---

### Post by batophobia on 2012-03-27
I agree that VirtualBox is a rather poor solution but if it is the only alternative then what else can I do?  But to answer some of your concerns, by "School PC" I mean the computer the school provided which no longer is acceptable as there is no network connections.  I was given the OK by my professor that I could take the HDD and use it in my personal computer, which I built myself and installed Windows & via a legal install disc.

From what I have seen so far, virtual box only required that I reformat the school HDD, which is ok since we did that in the beginning of class to do a fresh, complete Ubuntu install.  Also, I am putting Ubuntu on the Virtual Box, not Win7.

I have encountered a problem using Virtual Box, however.  I cannot SSH into the virtual Ubuntu machine and nothing I have seen online helps any (i.e. bridging connections and what-not).

---

### Post by Mark Phelps on 2012-03-27
Don't know why you're so bent on running BOTH OSs as the same time ... but if it was me, I'd keep it "simple" and have only one OS on each drive, and run only one OS at a time.

Problem is, what if you run into difficulties doing the classwork using VB?  Is the problem related to something you are doing in class? Is the problem due to a limitation of using a virtual environment? Is the problem due to a limitation of VirtualBox?

Class problems are challenging enough as is -- layering Virtualization on top of them could make them more difficult than they need to be.

---

### Post by batophobia on 2012-03-27
The problem is that I need my Linux OS running pretty much all the time for class purposes and while I could just use Linux for everything, I find it much easier to use my personal computer with Windows (mostly for gaming purposes since I am a huge gamer).

I was running one OS at a time for a while but it simply has not been working and I finally broke down yesterday and wiped the drive to try the Virtual Box suggestion.  As you suggested I found a few problems but the only substantial one is that I cannot SSH into my virtual machine.  If problems arise in the future based on the virtual machine then I will cross those bridges as they come, which I am ok with.

---

### Post by troymius on 2012-03-27
Your comp cannot run both Linux and Win in the same time, unless you run one of them in a virtual machine.

If you are ok with running Linux before lunch and Windows after lunch for example then simply setup dual boot and reboot at lunchtime.

---

### Post by batophobia on 2012-03-27
I have already accepted that they cannot run at the same time without some virtual interface (i.e. virtualbox).  I'm trying to figure out how to SSH into said virtual machine.

---

### Post by troymius on 2012-03-27
> **batophobia said:**
> I have already accepted that they cannot run at the same time without some virtual interface (i.e. virtualbox).  I'm trying to figure out how to SSH into said virtual machine.

I don't know how to do it but I do know that it can be done. For example, when you buy a web hosting virtual server (a common thing today) you can ssh to it from far away. 

This link explains how port forwarding can be used to achieve connection from host to guest...
[http://linuxconfig.org/unable-to-ssh-into-virtualbox-guest-machine](http://linuxconfig.org/unable-to-ssh-into-virtualbox-guest-machine)
...but it's a good start.

---

### Post by batophobia on 2012-03-28
Well I never got Virtual Box to work the way I wanted to so I got my laptop and just set it up as my school system.  Thanks for trying guys. I really wish it would have worked since my laptop is old and has some terrible hardware (making it really slow) plus there is not a good driver for my internal fan so it overheats often, but it is the best I can do.

---

