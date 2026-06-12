---
title: "I humbly request enlightenment."
date: 2009-06-09
forum: Installation &amp; Upgrades
---

### Post by Poinzy on 2009-06-09
Hello, I just wanted to take just a moment to introduce myself, say “Hello” and to request some advice, or at least get an opinion weather or not I am going about this the right way. I will do my best to keep this as short as possible. I guess to sum it up I am sick and tired of Microsoft's ********. I built my first computer (sometime in 1975) when I was 12 years old from a kit called the Altair. PC's Hardware/Software have been both my life long Hobby and my Career. From 8800, 8080, 8088, Texas Sinclair, TRS-80 (Trash-80 hehehe) ect. I went on to put my first BBS on-line at 16. Amazingly enough for what it's worth, I was turned off by the whole “Internet thing” (“Hi” I'm a 12 year old girl want to chat?) and was to busy with my career to ever make a dime off the Internet. I'm sorry I am “rabbling” At any rate, I went with the flow always staying on the cutting edge both with system components and OS's. The only exception was going from DOS to OS/2 because it ran games better then DOS could, due to the 64K – 640K thing, and not going to Windows till I got feed-up with the “Latest and Greatest” hardware taking so long to get OS/2 drivers. Any way my whole career was in Windows based Implementation, Integration and Coding, as of four years ago I retired from a fortune 100 as Vice President / Sr. Software Engineer. With all the Virus's, Spyware, lack of challenge left, worst of all Microsoft Activation, that now plaques Windows, I have made the decision to put all my time, efforts, and willingness to help others into Linux. I had “Played” with Linux a few times over the decades, however due to it's lack of cutting edge hardware support and my lack of knowledge on the Linux paradigm I never played long or much with it. After downloading Linux Mint 7 and Ubuntu like five or six day's ago and having the Live CD's come right up and run on my;  
 

 Intel DX58SO (Extreme Series)
 Intel Core i7-920
 6 Gig Ram
 Nvidea GeForce GTX-280
 3 - Seagate 1TB-32meg Cache SATA HD ST310005N1A1AS
 1 - Western Digital 1TB-8meg Cache SATA HD WD10EAVS
 

 Not only come right up but simply “SCREAM” I was thoroughly impressed!!! And after playing with it for a few hours, it was more than obvious to me that Linux has matured. Moving on probably needless to say I Multi-Boot and have since the DOS days with each game desiring and needing it's own unique configuration. I boot;
 

 1X – XP-64
 2X – Vista Ultimate-64
 

 Ever since like somewhere around Windows 1.1 (Windows for Workgroups) I have had multiple installations of windows. I simply put them into their own Pri-Partition on Disk-0 than hide the other Part from it. I have spent the last like 25 – 30 hours trying to get Linux into my current schema, with little to no success. Any way, after much thought and the decision to put my priority and time into Linux, I have decided to format, reconfigure, and reinstall all drives. While playing with the install and trying to get a little bit of understanding on how Linux works and reacts to stuff I have found that separate instance's of installations do not seem to mind sharing a single Swap part. Or a single “Home” mounting point. Is this correct? If this is across the board for different Distro's than if you would be kind enough to give me you opinion on this schema I would appreciate it.
 

 HD-0 4 equal part. 3 Pri 1 Ext.
 Part-0 Pri-250gig Vista-64
 Part-1 Pri-250gig Vista-Ult
                                  Part-2 Pri-250gig Win-7
 Part-3 Ext-250gig
     Logical Drives (For Linux)
     LD-0 (ext3) 5gig GRUB (Unless you can recommend a better boot loader?)
     LD-1 (ext3) 245gig “Home” Mount Point All (Linux Installs)
 

 

 HD-1 1 Pri. 1 Ext.
 Part-0 Pri-500gig (NTFS) Win Stuff
 Part-1 Ext 500gig
     Logical Drives (Linux “Root” Mount Points)
     LD-0 (ResierFS) 125gig Linux “\” Inst-1  
     LD-1 (ResierFS) 125gig Linux “\” Inst-2
     LD-2 (ResierFS) 125gig Linux “\” Inst-3
     LD-3 (ResierFS) 125gig Linux “\” Inst-4
 

 HD-2 1 Pri. 1 Linux Swap
 Part-0 Pri. 985-gig (NTFS) Win Stuff
 Part-1 SWAP 15gig (All Linux Inst)
 

 HD-3 (I'll Figure it out as needed)
 

 Questions;
 
[LIST=1]
[*]
[LIST=1]
[*]
[LIST=1]
[*]Do you see any “Issues”?
[*]Am I on the right track here?
[*]Previously asked, will separate             independent Installs\Distro's have an issue sharing “Home”
[*]Providing I give each install             the same first user account can they share the same folder?
[*]4 is there a way to use a folder             as a mount point?
[*]Any recommendation?
[*]Lastly; is there any imminent             danger that I should be aware of, or any “MUST” read that I             should know about?
[/LIST]
 
[/LIST]
 
[/LIST]
 

 In conclusion, I would like to thank you in advance for both your time and assistance. “Thank You!!” I look forward to being able to help others in the near future, and to be able to contribute to the Linux community as soon as I get up to speed...
 

 Best Regards,


Poinzy

 

 PS (Sorry) I apologise for being so winded and for draging this out. (Some of us have communication issues)

---

### Post by prshah on 2009-06-09
> **Poinzy said:**
> 
 Intel DX58SO (Extreme Series)
 Intel Core i7-920
 6 Gig Ram
 Nvidea GeForce GTX-280
 3 - Seagate 1TB-32meg Cache SATA HD ST310005N1A1AS
 1 - Western Digital 1TB-8meg Cache SATA HD WD10EAVS
 
I have decided to format, reconfigure, and reinstall all drives.

I have found that separate instance's of installations do not seem to mind sharing a single Swap part.

 Or a single “Home” mounting point. 

 Questions;
[*]Do you see any “Issues”?
[*]Am I on the right track here?
[*]Previously asked, will separate             independent Installs\Distro's have an issue sharing “Home”
[*]Providing I give each install             the same first user account can they share the same folder?
[*]4 is there a way to use a folder             as a mount point?
[*]Any recommendation?
[*]Lastly; is there any imminent             danger that I should be aware of, or any “MUST” read that I             should know about?


My first suggestion to you will be to use virtual machines, rather than create so many partitions just to try out various OSs. Install one primary operating system (preferably Ubuntu) and use the (included?) VirtualBox program, which is available in the repositories.

Second: Sharing the swap is absolutely not an issue; _provided_ you don't plan to use the hibernate feature in any of the linux OSs. Windows couldn't care less about swap partitions.

Third: Sorry, sharing home partition between OSs is out of the question. It's not impossible "per se", but it will definitely lead to breakage in each OS.

Fourth: Using a "folder" (directory) as a mount point is an essential part of any linux system. Yes you can do this; but I can't understand why this is important enough to be mentioned.. maybe you need to explain more about why this is important to you?

---

### Post by Poinzy on 2009-06-09
It's not a matter of &#8220;Trying out&#8221; Various OS's it is a matter of having different environments on hand for different aspects of computing. For instance I have always ran an OS instance for Gaming, another instance for Coding, and yet another as locked down as I can get it for Web Surfing, Downloading and trying &#8220;Stuff&#8221; which I really don't know where it comes from or if it will totally trash my system. I am sure that you can easily see that for instance; The environment priority for Gaming, are simply not  in the same ball park as the environment priorities for Development.
 

 As for mounting a directory as a drive, it would eliminate the need of resizing partition as one installation instance required more space and or another required less. Not to mention it also got my mind following a security paradigm of a parent directory not allowing access, and a child directory not inheriting the parents access list yet grating access. In my head the outcome would be only gaining access through a specific link to the child... Was just a thought, the mind goes where it choses and I tend to let mine roam...  
 

 Regards,


Poinzy

---

### Post by Ptero-4 on 2009-06-30
You don't really need multiple "instances" of Linux to do your stuff because Linux comes already pretty much locked down, also there's no "registry" that can get corrupted from installing and removing applications, which means that you can install and remove apps as much as you want and it won't "become slow", also the filesystems in linux (you got several to choose from) doesn't suffer from the fragmentation issue that fat32/ntfs suffers, and there's no malware to worry about neither.

---

### Post by presence1960 on 2009-06-30
> **Ptero-4 said:**
> You don't really need multiple "instances" of Linux to do your stuff because Linux comes already pretty much locked down, also there's no "registry" that can get corrupted from installing and removing applications, which means that you can install and remove apps as much as you want and it won't "become slow", also the filesystems in linux (you got several to choose from) doesn't suffer from the fragmentation issue that fat32/ntfs suffers, and there's no malware to worry about neither.

+1

How does that saying go ...Keep it simple! Until this evening I never made it through the original post.

---

