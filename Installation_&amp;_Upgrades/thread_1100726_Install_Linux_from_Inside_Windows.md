---
title: "Install Linux from Inside Windows"
date: 2009-03-19
forum: Installation &amp; Upgrades
---

### Post by adzik on 2009-03-19
This is another way I found I could install Linux without the capability of booting from USB or a CD. 
You know how it goes...when you need something you figure ways out to get it. It may offer a solution for anyone that is stuck in the same situation I was in - a Windows laptop that won't boot from USB and a dead CD/DVD drive. It is also relatively simple since it's all point and click, but I will say that it is by no means a 100% safe as far as your data is concerned.
It's more of a risky/fun option if you aren't concerned with whether it succeeds or fails and hoses your entire system in the process.
The install took place entirely from within Windows XP with a downloaded ISO image, to place a native gOS/Ubuntu install on the laptop. And no, it's not wubi, it's a real, native install.
Since I am not one for mucking up forums with info people may not want, have a look at the post [**_here_**]("http://thebrainbuzz.blogspot.com/2009/02/injecting-linux-onto-laptop-using.html") for the process I took.
It is a bit long-winded, so if you only want to read the steps taken to do this, scroll down a 1/3 of the page and start from there.

If anyone finds it useful, just let me know and I'll clean up and refine the process for more precision.
Hopefully you find this helpful.

---

### Post by Mark Phelps on 2009-03-19
If I read your post right, you installed a virtualization manager (in this case, Qemu), and then installed an OS (in this case, gOS) inside that virtual machine.

So, basically, you found another way to do what Wubi does.

The following is from the Qemu Wiki:

> ... thus it can be viewed as a hosted virtual machine monitor. It also provides an accelerated mode for supporting a mixture of binary translation (for kernel code) and native execution (for user code), in the same fashion as VMware Workstation and Microsoft Virtual PC.

VMWare Workstation and MS Virtual PC are virtualization tools.

But it's not a "native install"; it's a virtual machine.

---

### Post by adzik on 2009-03-19
I suppose you could say it's an alternative to wubi, but it is a native installation as it created the filesystem directly on a physical disk rather than a file on the Windows filesystem. Out of the free virtual machine managers out there, only Qemu seemed to be able access the physical disk and write directly to it.
I've already completed the process at this point and there is no more existing Windows XP installation on the laptop, just ubuntu :) .

---

### Post by Mark Phelps on 2009-03-20
That's certainly good to know.  

So, you were able to blow away the MS Windows install and simply keep the Qemu install -- without having to do a lot of work creating a new partition, loading LVM, migrating UBuntu, etc?

---

### Post by adzik on 2009-03-20
Yep, you got it, that's pretty much it.  I used Qemu to target the physical drive internally from Windows and overtake the system natively. So upon rebooting the laptop, there is an actual ubuntu(gOS) install. Much quicker and easier than the other options available, considering no USB or CD booting capability on this machine at this point.

---

### Post by Mark Phelps on 2009-03-20
Wow -- that's really impressive!!

You should consider putting your how-to into the tutorials section.  I'm sure that others would prefer the approach you have used to using Wubi, especially if it's a simple matter of making Ubuntu the only OS when done.

Well done!

---

### Post by adzik on 2009-03-21
Thanks. I'll do that.

---

### Post by baxzius on 2010-06-29
People i tried to do the following task..... 
you know one thing i had a laptop of dell model inspiron. i bought it @ second hand.
later i found dead cdrom and non-working usb....
i am developer toooooo.......
i thought i just wanna install linux. especially ubuntu linux. i have only 256 mb ram.
but later i tried to search in google. many forum and people suggested me to use wubi.
some people suggested to use unetbootin and some people said that debian based installer which helps to install linux through internet.....later i lost my windows booting file which is mbr.... this was my tragedy. but it led me to find a way to install ubuntu without 
cdrom and usb ;-)

**LOOK A IF ITS A LAPTOP OR PC... JUST REMOVE THE HARDDISK. AND CONNECT TO ANOTHER COMPUTER.PUT THE INSTALLATION CD INTO THE HOST COMPUTER  AND BOOT INTO DISTO LINUX OR UBUNTU LINUX. WHEN IT ASKS  INSTALLATION LOCATION. POINT TO YOUR SECONDARY HARD DISK WHICH IS YOUR LAP DISK OR PC DISK. IT  CREATES GRUB AND LINUX PARTITION WITHOUT LOSING WINDOWS IF YOU WISH.I BELEIVE NEXT YOU KNOW WHAT TO DO.**
ENJOY MY EXPERIENCE.

---

