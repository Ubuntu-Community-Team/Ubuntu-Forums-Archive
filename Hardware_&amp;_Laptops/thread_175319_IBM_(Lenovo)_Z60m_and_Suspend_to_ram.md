---
title: "IBM (Lenovo) Z60m and Suspend to ram"
date: 2006-05-13
forum: Hardware &amp; Laptops
---

### Post by miobio on 2006-05-13
Hellooooo!!!

I've just upgraded from breezy to dapper in the hope that suspend to ram will work on my IBM Z60m but it seems like it's not my lucky release yet :( 

Anyway here's the exact problem: If i suspend and resume within some minutes, everything works ok (I know it doesn't make any sense but please believe me, it's like that!!!!)

If i leave my nice Z60 there for some time under suspend... BOOOM!!! When i resume, either the hard disk hangs or the screen doesn't turn on :evil: [-( 

Now... I had a look around, I read (on a red hat forum I think) the HD's problem I have is a kind of common issue on these laptops and they were providing a kernel patch to solve this, unfortunately i can't find that page anymore and on all the Z60m tests I found suspend to ram was given as "working" :-k  


Anybody who has a Z60m and can give me a hand somehow??


This is my lspci for graphic card and SATA controller:

```
VGA compatible controller: ATI Technologies Inc M24 1P [Radeon Mobility X600]
```
```
IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
```

---

### Post by jrei on 2006-06-12
I have the same problem

---

### Post by chiron80 on 2006-06-19
[QUOTE=miobio]If i suspend and resume within some minutes, everything works ok

If i leave my nice Z60 there for some time under suspend... BOOOM!!! When i resume, either the hard disk hangs or the screen doesn't turn on

Now... I had a look around, I read (on a red hat forum I think) the HD's problem I have is a kind of common issue on these laptops and they were providing a kernel patch to solve this, unfortunately i can't find that page anymore and on all the Z60m tests I found suspend to ram was given as "working"[/QUOTE]

I am also experiencing the same problem. I can successfully suspend to RAM, and about 1/3 of the time I can resume properly, 1/3 of the time the laptop seems to resume correctly but I cannot run any applications (I get errors relating to the hard drive when running any application including 'reboot' or 'shutdown'), and 1/3 of the time the screen just does not come on at all. I haven't narrowed down which set of circumstances leads to which outcome.

I don't have my laptop in front of me, or the sheet of paper where I wrote down the error, but I will post back with the specific hard drive errors later.

I found a reference to errors with SATA and Linux on the ThinkWiki site here:
[Problems with SATA and Linux]("http://www.thinkwiki.org/wiki/Problems_with_SATA_and_Linux")

But according to the website, the necessary patches have been applied to the Ubuntu Breezy kernel. I assume this means the patch has been applied to the Dapper kernel as well (how can I confirm this?).

I will post again later with the error codes, and the results of some google searching.

- Ben

---

### Post by miobio on 2006-06-19
Thanks a lot for the help!!!!

---

### Post by Pluk on 2006-06-19
Pata here and same problem with a T42 :(

---

### Post by chiron80 on 2006-06-26
[QUOTE=chiron80]I am also experiencing the same problem. I don't have my laptop in front of me, or the sheet of paper where I wrote down the error, but I will post back with the specific hard drive errors later.[/QUOTE]
Sorry I didn't reply back sooner, but it seems that the problem has been resolved with my laptop!

I upgraded to kernel 2.6.15-25-686 (from 2.6.15-23-686), including upgrading several other packages. The most significant upgrade I believe is from acpi-support 0.84 to 0.85. In either case, the reason I never posted back was because I have been unable to reproduce the error since the upgrade.

I did however find the error codes I wrote down, and for completeness sake (and if other people are searching for this error), I will include them here:

```
sd 0:0:0:0: SCSI error: return code = 0x40000
end_request: I/O error, /dev/sda, sector nnnnnnn
```
Hope that others have had the same luck that I have had.

- Ben

---

