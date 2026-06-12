---
title: "4 Gigs of RAM"
date: 2008-12-04
forum: Hardware
---

### Post by dyous87 on 2008-12-04
Hello everyone,

I have a question regarding the maximum amount of RAM that Ubuntu can detect.

I currently have a laptop running 32 bit Ubuntu 8.04 with two gigs of RAM and I was thinking of upgrading it to four gigs. I am unsure if 32 bit Ubuntu will be able to detect up to four gigs. I tried googling for the answerer and read many different conflicting resorts. Some said you need the 64 bit Ubuntu for all 4 gigs, while others said it is possible but with a slight processor performance hit.   

What do you think the best thing I should do is? Will Ubuntu recognize and play well with 4 gigs of RAM out of the box. The reason I am sticking with 32 bit for now is because it just seems better supported to me. I tried 64 bit in the past and had lots of problems with flash, sound and vitualbox which I use a lot.

Thank you in advance for your suggestions,
David

---

### Post by goldenphoenix713 on 2008-12-04
As far as I know, all 32-bit operating systems can only detect up to 3.5 GB of RAM.  For Ubuntu, 3.5GB is really not necessary, unless you like to have A LOT of programs running at the same time.  I chose to add 4GB (and thus, really 3.5GB) because I'm dualbooting with Vista, where it's much more needed.

---

### Post by meho_r on 2008-12-04
Maybe you should try 64-bit version now. You can install java (OpenJDK or Sun) and flash from repos, no need for hacking anymore. Add Sun's repo for VirtualBox (or use ose that can be found in repos) and there you go. That's it. And, after all, you can try all this from LiveCD, just in case ;)

---

### Post by scorp123 on 2008-12-04
> **dyous87 said:**
>  I currently have a laptop running 32 bit Ubuntu 8.04 with two gigs of RAM and I was thinking of upgrading it to four gigs.  What's the CPU in your laptop? And how old is your laptop? If the BIOS and/or CPU is too old they will not be able to detect more than ~3 GB of RAM.

I myself have a 32-bit "Core Duo" Laptop and I know for sure that it cannot handle 4 GB of RAM. But 3 GB of RAM work OK.

> **dyous87 said:**
>  I am unsure if 32 bit Ubuntu will be able to detect up to four gigs. You need the "Physical Address Extension" (PAE) feature compiled into your kernel. You can do this yourself ... Or if you are as lazy as me, you can follow this guide here and download the kernel image that "Ubuntu Server" uses (basically the same kernel as on the desktop version; except some professional features typically found on servers are turned on):

"Use more than 3GB RAM on 32-bit Ubuntu 8.04"
[http://samiux.wordpress.com/2008/06/15/use-more-than-3gb-ram-on-32-bit-ubuntu-804/](http://samiux.wordpress.com/2008/06/15/use-more-than-3gb-ram-on-32-bit-ubuntu-804/)

---

### Post by andreasis on 2008-12-04
Hi dyous87,

I agree that you should try the 64bit version.

On average I will have about 10 foxes open, a few programs running scripts in the background, a spreadsheet program, bittorrent, ftp, and ssh open, vmware server running windows xp, and I use preload.  I can say that, after 6 months of using Ubuntu, I have not seen my memory usage go over 2GiB.

That said, I do have 4GiB of ram installed, and I am using Intrepid x86_64.

Ubuntu offers the latest version of flash (10) from the repositories, and it works very well.  When watching youtube fullscreen, you just have to right-click>settings>disable hardware acceleration, but I haven't noticed any drops in performance (not sure if that's an issue for 32bit version). Java, as has been said, is not a problem.

There are certain advantages of 64bit, which I will not dive into here, but even with 2GiB of memory, if you have the capable hardware, I would give it a try.  How long ago did you try 64bit Ubuntu, which you say caused you trouble with your sound?

---

### Post by scorp123 on 2008-12-04
> **dyous87 said:**
> The reason I am sticking with 32 bit for now is because it just seems better supported to me. I tried 64 bit in the past and had lots of problems Dumb me ... I did not see that part.

Yes, you can follow these instructions then:
[http://samiux.wordpress.com/2008/06/15/use-more-than-3gb-ram-on-32-bit-ubuntu-804/](http://samiux.wordpress.com/2008/06/15/use-more-than-3gb-ram-on-32-bit-ubuntu-804/)

My desktop has a 64-bit capable quad-core CPU but for various reasons (e.g. commercial apps that refuse to work on 64-bit Linux) I too have to stick with 32-bit + PAE. No problems so far and I see my full 8 GB of RAM.

---

### Post by dyous87 on 2008-12-04
Thank you so much for all of your replies!

I have a Intel Core 2 Duo on a Sony Vaio VGN-FZ140E. It is about a year old now and running a 64 bit operating system will not be a problem. I actually think that it came pre-loaded with 64bit vista though I cannot check now because I have wiped it out long ago. 

Anyway I am going to give it a shot and see how it runs for me now. Just a couple of questions first though. I use virtualbox for running a 32 bit version of Windows XP Professional. I need to run this since I require Adobe CS3 (Flash, Photoshop, Fireworks) for my work. Will running the 32 bit Windows be a problem on a 64 bit host OS and a 64 bit virtualbox?

Also you have said that flash anad Java should no longer be a problem, how about 3d acceleration and compiz etc.?

Thank you again for your help and advice!
David

---

### Post by binbash on 2008-12-04
> **goldenphoenix713 said:**
> As far as I know, all 32-bit operating systems can only detect up to 3.5 GB of RAM.  For Ubuntu, 3.5GB is really not necessary, unless you like to have A LOT of programs running at the same time.  I chose to add 4GB (and thus, really 3.5GB) because I'm dualbooting with Vista, where it's much more needed.

No it is not true, my server is 32 bit and has 8 gb ram.

---

### Post by scorp123 on 2008-12-04
> **goldenphoenix713 said:**
> As far as I know, all 32-bit operating systems can only detect up to 3.5 GB of RAM.  True only if you don't enable "Physical Address Extension" (PAE). With PAE enabled a 32-bit OS can see up to 64 GB RAM. :)

---

### Post by scorp123 on 2008-12-04
> **binbash said:**
> No it is not true, my server is 32 bit and has 8 gb ram. He's right for as long "PAE" is not enabled. 
[INDENT]32-bit: 2^32 = 4294967296 Bytes = 4194304 KB = 4096 MB = 4 GB[/INDENT]

PAE uses a trick and increases the address space to 36-bit:
[INDENT]2^36 = 68719476736 Bytes = 64 GB[/INDENT]

But you have to enable that feature or your OS won't see any of the extra memory.

---

### Post by TyTiger on 2008-12-04
> **scorp123 said:**
> True only if you don't enable "Physical Address Extension" (PAE). With PAE enabled a 32-bit OS can see up to 64 GB RAM. :)

So then the answer to this thread is, Yes enable PAE and 32bit ubuntu will be able to see all 4GB's of RAM.

Next question, How.

---

### Post by scorp123 on 2008-12-04
> **TyTiger said:**
> Next question, How. Ahemmm ... How about posting nr. #4 in this thread? :D

---

### Post by omegamike3 on 2008-12-04
I believe that enabling PAE requires a recompile of the kernel. As a shortcut, you could install the server kernel which already has PAE enabled.

---

### Post by meho_r on 2008-12-04
> **dyous87 said:**
> 
I use virtualbox for running a 32 bit version of Windows XP Professional. I need to run this since I require Adobe CS3 (Flash, Photoshop, Fireworks) for my work. Will running the 32 bit Windows be a problem on a 64 bit host OS and a 64 bit virtualbox?

Also you have said that flash anad Java should no longer be a problem, how about 3d acceleration and compiz etc.?

Thank you again for your help and advice!
David

No problem regarding VBox, in fact, with VBox 2 you can host 32bit as well as 64bit guest systems.

3d acceleration is matter of your graphic card. In any case, try it from LiveCD before installation. You can install full compiz temporary while running LiveCD and test it. BTW, I have Ati Radeon x1650 Pro graphic card and everything works just fine, full blown compiz ;)

---

### Post by Cracauer on 2008-12-04
As mentioned, with PAE in the kernel you can make a 32 bit OS see RAM above 4 GB.

I need to add that if you have exactly 4 GB you need one other component to see all 4 GB: a BIOS with working remapping.

The space below 4 GB (depending on machine is can be 3.2-4 GB, 3.5-4GB, 3.8-4 or anything in between) is occupied by the PCI devices. RAM in that region is disabled.

What you need is a BIOS that can remap this RAM to be above 4 GB. So that the RAM that was on 3.5-4 GB is now at 4-4.5 GB.

Then, you will actually see 4 GB is you have a PAE kernel or a 64 bit kernel. You have RAM at 0-3.5 and 4-4.5 GB for a total of 1 GB.

Without working remapping PAE or 64 bit kernel do nothing. If you plugged in 8 GB with no working remapping you'd get 7.5 (or 7.3 or whatever) GB.

---

