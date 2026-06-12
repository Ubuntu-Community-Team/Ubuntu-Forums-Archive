---
title: "Daily System Freezes?"
date: 2006-09-25
forum: Hardware &amp; Laptops
---

### Post by glenduncanscott on 2006-09-25
Hi,

I'm relatively new to the world of Linux (June 06) but have been struggling to get a stable Ubuntu system working for months now. View my system here:

[https://wiki.ubuntu.com/LaptopTestingTeam/ToshibaSatelliteProA100](https://wiki.ubuntu.com/LaptopTestingTeam/ToshibaSatelliteProA100)

Everything normally installs ok and appears to work fine but then I suffer with daily system lockups. I can't do anything except for pressing the big red button. Windows was never this bad! This later results in fsck being run and sometimes having to rebuild the entire system again. This is a very time consuming process and very inconvenient. Often Synaptic Package Manager causes alot of the freezes, but it can also happen randomly with multiple apps running. Is there some conflicting software/hardware issues that i am not aware of? I know this description is very broad but if someone could kindly walk me through to finding a solution it would be much appreciated.

Cheers Glen

---

### Post by Trekos on 2006-09-25
Have you uninstalled Windows from your laptop ? (I assume it came with it, preinstalled, right?).
If it is still installed, you might want to check to see if you get the same crashes if you perform similar tasks (surf the web, write a document on OpenOffice).
'Cause it surely sounds a lot like a hardware issue (RAM) and it would be advisable to check out that possibility first.
Chose the memtest option from Grub (bootloader), let it run and see what results it comes out with.

---

### Post by glenduncanscott on 2006-09-25
No I'm running a dual boot system at present, even though I no longer use Windows XP, and yes it came preinstalled with Windows XP. I thought this might be part of the problem.

Since I've never run memtest what exactly should I be looking for when the results are produced or will it be obvious? 

Also should I use gparted to remove Windows or do I need to rebuild the system again from scratch? Thanks for your help. Glen

---

### Post by glenduncanscott on 2006-09-25
Ok I have run the memtest for 1 hour resulting in 6 passes and 0 errors produced. I hope this was long enough?

Also I have completely removed Windows XP using Gparted.

Will report any further system freezes in the next two days.

---

### Post by glenduncanscott on 2006-09-25
System froze yet again!!! Now performing a clean reinstallation of Ubuntu with no Windows XP! I hope this works!

---

### Post by coffeecat on 2006-09-26
I had the same problem on one of my machines. Near-daily lock-ups necessitating pressing the reset button. And like you the RAM passed the memtest, even though it was the RAM that was the problem.

A couple of points. Windows is more tolerant of faulty RAM than Linux. Can't remember the details, but something to do with the way Linux accesses the whole of available RAM I believe. Also, you may have to run memtest for 24 hours or more before getting an error and even then some faulty RAM will pass.

In my case I had two identical sticks in a dual memory configuration. I tried removing one and very soon got another freeze-up. 'Good,' I thought, 'I've found which one is faulty.' So I put the other stick in and got another freeze-up. :( Then I tried a RAM stick from another machine and everything worked fine. No freeze-ups. Clearly not one but two faulty sticks. Lightning does strike twice. And it's often said that faulty RAM is the commonest cause of issues like this.

Can you get hold of a RAM stick from somewhere to try in your machine and do what I did? Might be a more reliable test than memtest. If you still get freeze-ups look for another hardware problem. If not, you know you have faulty RAM.

---

### Post by wieman01 on 2006-09-26
I tend to agree wit Coffeecat. This sounds like a serious hardware issue, most likely the RAM. Just to re-confirm that.

---

### Post by SkyNet2029 on 2006-09-26
I had been dealing with the same issue in regards the 'daily lockups' on one of my machines, ran the memtest for 6 hours straight with no errors so went off in a different direction for a fix. 
While downloading files using Konqueror, aptitude, and especially adept (More than likely due to the larger download sizes on a fresh installation, no doubt) the system would hang. No response from the keyboard for at least 30-40 seconds (shift key cause it lights up, etc.)
and then I would get alot of disk-thrashing but that would do the trick. Until the next large download. 
What finally solved things for me was to set hdparm to disable DMA on my drives on that machine and it has not locked up ever since (I downloaded PCBSD this past weekend without a snag). I am still not sure why this works on my machine but have tried it out on another one I slapped together with identical parts from my junk heap after I confirmed that it too did the daily lockup on downloads. I suspect it is more tied to the way linux doesn't immediately commit to disk a file system change than to the actual way Linux 'runs in Ram'.
Anyway,
```
$sudo hdparm -d0 /dev/xxx
```
disables the DMA on the drive(s). 
Out of curiosity, my lockups matched in download size the amount of 
/tmpfs space available as shown on the output of 
```
#df -h
```.
(Once the available space in /tmpfs was used, the machine would not dump the file space to disk fast enough it seems.
Sorry for the long post, hope that helps in some way.

---

### Post by glenduncanscott on 2006-09-26
Have since performed the reinstallation and have only downloaded and only installed the system updates, then I rebooted which caused another system freeze! The only keys that appear to work are Alt+SysReq+B. This could very well be a RAM issue.

Thanks for your suggestions coffeecat, I'll run the memtest for 24 hours and post the results of any errors found. Also I'll have to order in some new RAM as I don't have any that is compatiable with this machine. Might take a few days.

Thanks for your suggestions Skynet2029 I will try those commands after I've systematically carried out the above. 

Thanks again for all your help, I'm glad my problems are not unique.

Cheers Glen

---

### Post by glenduncanscott on 2006-09-27
Memtest completed after 24 hours resulting in 146 passes and 0 errors produced. If this RAM is faulty it appears to be passing with flying colours. Will wait for the new RAM to arrive to see if any positive changes occur.

---

### Post by glenduncanscott on 2006-09-27
I don't appear to be any further forward so I thought I'd try Skynet2029's suggestions:

> glen@SatPro:~$ sudo hdparm -d0 /dev/sda1

Should this be the expected result? Is DMA now off?

> /dev/sda1:
 setting using_dma to 0 (off)
 HDIO_SET_DMA failed: Inappropriate ioctl for device

> glen@SatPro:~$ df -h
Filesystem            Size Used Avail Use% Mounted on
/dev/sda1              37G  2.9G   32G   9% /
varrun                 93M   88K   93M   1% /var/run
varlock                93M  4.0K   93M   1% /var/lock
udev                   93M   92K   93M   1% /dev
devshm                 93M     0   93M   0% /dev/shm
lrm                    93M   19M   75M  20% /lib/modules/2.6.15-27-386/volatile

---

### Post by SkyNet2029 on 2006-09-27
>  setting using_dma to 0 (off)
HDIO_SET_DMA failed: Inappropriate ioctl for device

means the answer is no because your drive hates DMA off. (that's the inappropriate part of the ioctl for device bit.

I was suggesting the DMA set to off since some (most of my machines) setups can't reallocate (something more to do with the way the MMU is (or isn't) utilized) the memory fast enough to allow for DMA to be on, causing a bottleneck on the drive controller/CPU and hence the locking up. 

Sorry that isn't woking for you.
You can verify the DMA settings abit easier with this:

```
$hdparm -i /dev/xxx
```

in that (i)nformation that is barfs up in a console is a line that lists
all (u)dma available and where it is set at is denoted by a small asterisk.

Although since your hdd won't allow that to be turned off, it really doesn't matter too much, although could still be the culprit. Dunno.

---

### Post by glenduncanscott on 2006-09-27
Tried your suggestion but had a similar result as before:

> glen@SatPro:~$ sudo hdparm -i /dev/sda

/dev/sda:
 HDIO_GET_IDENTITY failed: Inappropriate ioctl for device

Anyone have any further suggestions?

---

### Post by glenduncanscott on 2006-09-30
Still unable to resolve this issue. Have noticed this repeated error message which could be partly responsible. 

> ACPI-0307: *** Error: No installed handler for fixed event

I have temporarily disabled the acpi and acpid in the Boot Up Manager and everything appears stable thus far. Any suggestions for finding a better solution that would allow acpi to be enabled would be much appreciated?

---

### Post by ethan961 on 2006-10-02
I wish you good luck!

---

### Post by glenduncanscott on 2006-10-02
Thanks for the sentiment ;)

Brains will only get you so far and luck always runs out.

---

### Post by glenduncanscott on 2006-10-16
After another rebuild with no drivers installed system still froze with no explaination. It would appear this system is not linux compatiable. After 4 months of fustration I'd had enough and sold it today...problem solved! Thanks for all you input.

---

