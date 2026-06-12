---
title: "How Do I Check Whether My Hard Driver Is In Fact Empty?"
date: 2010-09-07
forum: Hardware
---

### Post by Will1 on 2010-09-07
Hi,

I somewhat recently decided to wipe my hard drive blank and I did so I believe by writing all the 0's to 1's or the 1's to 0's or something like that. My question is though, now that it is unformatted, how I can check that it is truly 100% blank?

I have so far tried the Disk Utility which read:

320 GB Hard Disk
320 GB / 298 GiB / 320,072,933,376 bytes

but I do not know whether it's 100% blank by that because it is not in a % nor is it comparable to anything I know of, i.e. total size of the drive in bytes (would that be written on the drive itself and therefore give me the number I needed to confirm it is in fact 100% blank?)

I also tried GParted which read:

unallocated
298.0 GiB

with what I can tell is a 100% grey background but I am not confident enough in myself to conclude that that would mean it is a 100% blank drive. If someone else could confirm that for me, with the source, then that would be great.

I too tried Disk Usage Analyzer and [Google]("http://www.google.com.au/url?sa=p&pref=ig&pval=3&q=http://www.google.com.au/ig%3Fhl%3Den%26source%3Diglk&usg=AFQjCNH1kEen7nYvAop6K_53cfXVwWQinQ") but because my drive is not formatted I didn't have much luck there.

If I didn't make it clear, what I am trying to do is confirm to me that my hard drive is in fact 100% empty, beyond any reasonable doubt and I found that I am having a hard time doing that. Any help would be greatly appreciated.

Thank you.

Edit: I just realised I posted in the wrong area. Could a moderator please move it to the proper one, I think General, it would be much appreciated. Thank you.

---

### Post by gzarkadas on 2010-09-08
The sizes are ok, you don't have to worry about them.

```

320 GB = 320*(1000)^3 = 298 GiB (note the i in between) = 298 * (1024)^3

```Now to check whether your drive is empty is a task that needs some thought. It is faster to rewrite it with zeroes and be content if no errors are reported than read it and verify that everything read is zeroes (sampling some sectors in this case is obviously not enough).

So I would suggest to find (say with Gparted) what device identifies your drive (for example, lets assume it is /dev/sdb). _**IMPORTANT**: You must do this right, else you will **destroy** another, good one drive. _Then, issue this command:```

sudo shred -n1 <target-drive>

```In our example you would put there /dev/sdb instead of <target-drive>. In your real case, put there the device that identifies your drive-to-wipe-out.

PS: There is a strong argument that a single pass is enough in modern disks  (make a search in the forum if you want more information). If however (i) you are sceptical about this, (ii) you need to be absolutely certain that any data is wiped out for ever and (iii) you don't mind letting the computer burn some extra watts and take 3 times as much to finish, then remove the -n1 switch, so that shred will perform the default number of passes (3).

---

### Post by Sobuntu88 on 2010-12-09
Hello,

I am having a shred issue. I hope you can help. I am using Ubuntu 10.10 and I am trying to shred a drive connected to a Thermaltake BlackX. It is connected using USB. I have shred'ed multiple drives using the same method. With success. This is the only drive giving me problems. I started off using the command: [sudo shred -vfz -n 7 /dev/sdb1] which worked for 2 passes and the returned: [shred: /dev/sdb: fdatasync failed: Input/output error] I have umounted the drive and retried several times. The drive will now do zero passes and returns the same error. I also tried the [sudo shred -n1 /dev/sdb1] which seemed to start working for about 20-25 minutes and then it returns the same error. Cna you help please?

---

