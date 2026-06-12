---
title: "Trying to do a clean install of Windows over an encrypted Ubuntu install"
date: 2008-10-15
forum: General Help
---

### Post by diablo75 on 2008-10-15
I don't know if this is an isolated problem or not so I'm shooting this out there to see if it's happened to anyone else.

A friend of mine is just dying to get back into his native, virus ridden Windows environment after I had him try Ubuntu out.  He's a very obsessive-compulsive person (particularly with the way fonts are rendered).  I tried to convert him.  Most people would shrug, but I'm the person who has to fix this box every time he manages to screw it up...

Anyway, upon booting off his Dell provided Windows XP CD, the "Press Any Key to Boot From CD" appears.  You press a key, it starts with the "Windows is inspecting the hardware...".... and then, completely black screen with no CD-ROM activity.

Since VirtualBox is still on the Ubuntu machine, I decided to see if that disc will boot in a fake environment and it does.  But it fails to boot in a native environment.  This has never happened to me before... but this is also the first system I've ever installed with an encrypted volume.

So I'm wondering if the encrypted volume and the Windows install CD are having a conflict of some kind.  If that's the case, could I clear the HD up with GParted first?  Or would that be a waste of time.  I don't want to end up stuck with a dead machine and a Windows install CD that doesn't want to boot like it should...

---

### Post by Soepstengel on 2008-11-16
I have the exact same problem.

There are three partitions on my hard disk. An encrypted partition which contains my Ubuntu 8.10 installation, a /boot partition to boot from and to encrypt/decrypt the data, and a completely empty NTFS partition.

When I boot from the Windows XP installation cd I get the same problem as described in the post above. This also occurs when I boot from the Windows Vista installation cd.

Any idea's on what causes this problem and/or how to solve it are more then welcome.

---

### Post by Therion on 2008-11-16
If you want to do a clean install you could create a GPartEd LiveCD, boot to that CD and use it to delete the existing partitions on the hard drive you want to install on.

---

### Post by Soepstengel on 2008-11-16
> **Therion said:**
> If you want to do a clean install you could create a GPartEd LiveCD, boot to that CD and use it to delete the existing partitions on the hard drive you want to install on.

Thanks for your reply. But I want to install Windows XP on the NTFS partition without removing or modifying my other partitions.

---

### Post by diablo75 on 2008-11-17
Just for the record I had to use gparted to remove the partitions on the HD before I could get the factory XP CD to boot and install the OS successfully (it's been a while since I posted this thread and ended up resorting to gparted to finish things).  I'm not the person to say or know why this is, but all I know is that deleting the encrypted partition allowed me to boot the CD.

---

### Post by TeXtonyx on 2008-11-17
> **Soepstengel said:**
> Thanks for your reply. But I want to install Windows XP on the NTFS partition without removing or modifying my other partitions.

Some of the Windows cds do not provide an update install. They
require an install to a clean drive. That's true whether there
is an encrypted partition or not. Find a cd that lets you do a
non-destructive reinstall of Windows to C:\Windows.000 

Test the cd on a healthy XP system that has Ubuntu installed on a
non-encrypted partition. You can stop the reinstall just short of
actually reinstalling to C:\Windows.000. You don't get that far
in your situation. This approach tests whether it is the cd being
used or whether the encrypted partition which prevents install.
Do you have a test computer, or actually just a spare hard drive? 
 
That C:\Windows.000 will defeat most viruses which are embedded 
in the old OS, now. And leave nearly all the data untouched except 
for My Documents. But very few of the applications will work, they
will need to be reinstalled. I like the fonts better in Thunderbird
in Ubuntu than I do in Windows.

---

### Post by Soepstengel on 2008-11-19
> **TeXtonyx said:**
> Some of the Windows cds do not provide an update install. They
require an install to a clean drive. That's true whether there
is an encrypted partition or not. Find a cd that lets you do a
non-destructive reinstall of Windows to C:\Windows.000 

Test the cd on a healthy XP system that has Ubuntu installed on a
non-encrypted partition. You can stop the reinstall just short of
actually reinstalling to C:\Windows.000. You don't get that far
in your situation. This approach tests whether it is the cd being
used or whether the encrypted partition which prevents install.
Do you have a test computer, or actually just a spare hard drive? 
 
That C:\Windows.000 will defeat most viruses which are embedded 
in the old OS, now. And leave nearly all the data untouched except 
for My Documents. But very few of the applications will work, they
will need to be reinstalled. I like the fonts better in Thunderbird
in Ubuntu than I do in Windows.

I have an original good working Windows XP CD which supports re-installation of a Windows XP installation. I tested your idea on an other computer which has Windows XP installed and Ubuntu installed in a non encrypted partition.

It worked fine and in the end I had an extra Windows.0 folder on the C: partition. The exact same CD doesn't work on the computer with the encrypted Ubuntu installation.

I'm thinking that the encrypted partition is causing the problem.

---

### Post by TeXtonyx on 2008-11-19
"You can stop the reinstall just short of actually reinstalling to 
C:\Windows.000. You don't get that far in your situation." 

'It worked fine and in the end I had an extra Windows.0 folder on 
the C: partition. The exact same CD doesn't work on the computer 
with the encrypted Ubuntu installation.

I'm thinking that the encrypted partition is causing the problem.'

I'm thinking so too. Unencrypting the partition now and after the
XP install, applying encryption again is not an option?

---

### Post by Soepstengel on 2008-11-19
> **TeXtonyx said:**
> "You can stop the reinstall just short of actually reinstalling to 
C:\Windows.000. You don't get that far in your situation." 

'It worked fine and in the end I had an extra Windows.0 folder on 
the C: partition. The exact same CD doesn't work on the computer 
with the encrypted Ubuntu installation.

I'm thinking that the encrypted partition is causing the problem.'

I'm thinking so too. Unencrypting the partition now and after the
XP install, applying encryption again is not an option?

I don't think it's possible to unencrypt everything and after the instllation of XP encrypt everything again.

---

