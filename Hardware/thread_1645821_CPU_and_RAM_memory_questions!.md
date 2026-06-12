---
title: "CPU and RAM memory questions!"
date: 2010-12-15
forum: Hardware
---

### Post by communityofexcellence on 2010-12-15
So, I have a strange question which I haven't managed to find the answer to but I'm sure this wonderful and knowledgeable community could aid me.

I was curious on whether or not there was non volatile memory in either of the two. Or any way to keep an amount of code residing in them after deprivation of current.

Would this be possible?

OT: are security questions related to windows systems prohibited in the security forum?
Thanks in advance!

---

### Post by cascade9 on 2010-12-15
There is (or at least there was) a tiny amount of memory on CPUs that is non-volatile. Intel used to mark CPUs with serial numbers (and probably still do!), and it wasnt in the BIOS. I dont know if that memory would be writable, but I'd assume so. 

You can also recover the contents of RAM- 

[http://blogs.gnome.org/muelli/2010/04/reading-ram-using-firewire/](http://blogs.gnome.org/muelli/2010/04/reading-ram-using-firewire/)

---

### Post by communityofexcellence on 2010-12-15
But the data inside the ram would be immediately erased after shutdown/removal from the tower, correct? 
As for that cpu memory, why is it never spoken of? This is the first time I've ever heard of it.

Or would it not exist in their new core i's?

---

### Post by cascade9 on 2010-12-15
> **communityofexcellence said:**
> But the data inside the ram would be immediately erased after shutdown/removal from the tower, correct? 
As for that cpu memory, why is it never spoken of? This is the first time I've ever heard of it.

Or would it not exist in their new core i's?

The data residing on RAM is erased, but its not instant. It takes a few seconds (or longer depending on power) to clear. To get more info, read the link I postred ;) 

As for the memory on the CPU, it probably only a tiny amount, and its not useable by the OS so its not really talked about at all. Its quite possible that it would exist on the core iX CPUs, but I dont know for sure.

---

### Post by communityofexcellence on 2010-12-15
So the memory on the cpu is entirely isolated from the system? You said its used for an ID, is this for like forensics or something? Why is it even there?

---

### Post by cascade9 on 2010-12-15
> **communityofexcellence said:**
> So the memory on the cpu is entirely isolated from the system? You said its used for an ID, is this for like forensics or something? Why is it even there?

You can read intels propaganda on the "Processor Serial Number" (PSN)here- 

[http://www.intel.com/support/processors/pentiumiii/sb/cs-007579.htm](http://www.intel.com/support/processors/pentiumiii/sb/cs-007579.htm)

The 'feature' was removed (or at least blocked) with the later P3s and P4s onward, mainly because the european Parliment was thinking about banning P3 CPUs with PSN due to privacy and vunrability concerns. 

[http://edition.cnn.com/TECH/computing/9911/29/eu.p3.ban.idg/index.html](http://edition.cnn.com/TECH/computing/9911/29/eu.p3.ban.idg/index.html)

---

### Post by communityofexcellence on 2010-12-15
So then if a few minutes have elapsed with lack of current to the ram and the psn feature no longer in intel cpu's its therefore impossible for code to reside in the ram or the cpu, correct?

Your help has been very useful and is greatly appreciated.

---

### Post by cascade9 on 2010-12-15
Theres no way AFAIK. 

Well, it might be possible in theory to read the last current RAM state once the RAM has been fully powered down, and its never been shown in pratice...again AFAIK. 

Sorry for the 'AFAIK' disclaimers, but even if I was an engineer at intel, I could never say for sure what could/should be in AMD or VIA x86 CPUs, and vice versa. 

BTW, from this story here it looks like at least some of the upcoming CPUs/mothbaord combos must have more writable RAM (non-volitile) somewhere- 

[http://www.infowars.com/remote-kill-switch-added-to-intels-newest-processor/](http://www.infowars.com/remote-kill-switch-added-to-intels-newest-processor/)

Of course, the info that would give the 'kill switch state' could be in the BIOS (or EFI, but then flashing to a new BIOS could isable the kill switch state...maybe? )

---

### Post by communityofexcellence on 2010-12-15
But that kill switch function is valid only on the sandy bridge technology, meaning that after pentium iii and before sandy bridge no permanent memory would be on the cpu, yes?

As for recovering the last ram state, how could this be done? Don't all the capacitors lose their data upon loss of current?

---

### Post by akand074 on 2010-12-15
Cache is memory. Which a CPU has. If I may ask, why would you want/need non-volatile memory on your CPU/RAM? Or is this just out of random curiosity? Even if they do (which they don't as far as I'm aware) they wouldn't be useable outside itself. So really, it would be as good as non-existent.

---

### Post by communityofexcellence on 2010-12-15
Thank you for your interest akand, and yes I am simply curious. It is also related to security. I am trying to find out if you could permanently store malicious code in non volatile memory inside the ram or the cpu and force it to load. As you've probably heard of virii residing in the ram and reloading itself if not properly discharged. I was just wondering if it could be taken to the next level.

PS: nice rig you've got there!

---

### Post by akand074 on 2010-12-15
> **communityofexcellence said:**
> Thank you for your interest akand, and yes I am simply curious. It is also related to security. I am trying to find out if you could permanently store malicious code in non volatile memory inside the ram or the cpu and force it to load. As you've probably heard of virii residing in the ram and reloading itself if not properly discharged. I was just wondering if it could be taken to the next level.

PS: nice rig you've got there!

I wouldn't imagine you have anything to worry about. And thank you. I apparently have a problem for the completely unnecessary.

---

### Post by communityofexcellence on 2010-12-16
:D
so then the conclusion would be that unless its a manufacturer secret, there is no way to permanently store data on a cpu or ram after a few minutes after shutdown, yes?

---

### Post by cascade9 on 2010-12-16
> **communityofexcellence said:**
> But that kill switch function is valid only on the sandy bridge technology, meaning that after pentium iii and before sandy bridge no permanent memory would be on the cpu, yes?

I wouldnt make that assumption.....

> **communityofexcellence said:**
> As for recovering the last ram state, how could this be done? Don't all the capacitors lose their data upon loss of current?

Capacitors dont store data. As for how (in theory) its possible to read the last RAM state, its like reading from HDD sectors that have been overwritten. Its just a lot harder.

> **communityofexcellence said:**
> Thank you for your interest akand, and yes I am simply curious. It is also related to security. I am trying to find out if you could permanently store malicious code in non volatile memory inside the ram or the cpu and force it to load. As you've probably heard of virii residing in the ram and reloading itself if not properly discharged. I was just wondering if it could be taken to the next level.

PS: nice rig you've got there!

The chance of storing code, of any kind on the non-volatile RAM in the CPU is so low its not funny. Even if it was run, its probably only a few bytes, maybe a kilobyte. 

BTW, the plural of 'virus' is 'viruses'. 

[http://linuxmafia.com/~rick/faq/plural-of-virus.html]("http://linuxmafia.com/%7Erick/faq/plural-of-virus.html")

---

### Post by communityofexcellence on 2010-12-16
Would the os be able to acess it anyway? Would it not be immediately overwritten in both cases?

---

### Post by cascade9 on 2010-12-16
The OS sure can see the PSN, with software. No idea on the 'kill switch' yet, but I'd gues that it is able to be seen by the OS, somehow.

---

### Post by communityofexcellence on 2010-12-16
I mean if it were overwritten with malware, could it do anything? Or is that like not possible?

---

### Post by cascade9 on 2010-12-16
*shuggs*. I have no idea. 

Its possible it could do something, but without actually having any data on the internal memory then its pure guesswork.

---

### Post by communityofexcellence on 2010-12-16
No no, I mean storing malicious code on the chip. Would it be able to load and infect the bios or the os?

---

### Post by cascade9 on 2010-12-16
Thats what I meant by 'I have no idea'. 

I think its in theory possible, but I cant say for sure.....

---

### Post by communityofexcellence on 2010-12-16
Oh, sorry. I didn't realize you meant information when you said data. Ok, I guess I will try in the security forum rather and see if anyone there knows anything else. Thanks a lot for your help!

---

