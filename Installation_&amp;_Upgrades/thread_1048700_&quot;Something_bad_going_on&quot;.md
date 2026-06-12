---
title: "&quot;Something bad going on&quot;"
date: 2009-01-23
forum: Installation &amp; Upgrades
---

### Post by chaotos on 2009-01-23
I am trying to install Ubuntu on my Gigabyte GA-MA69G-S3H motherboard with a AMD Athlon 64x2 4400 Brisbane 2.3 GHz processor. I am using the onboard video.

After "scanning the mirror" the installation screen fades to black. Then I see several line ending with "checking battery state". Then an error message "The display server has shut down 6 times in the last 90 seconds. It is likely something bad is going on."

Must be. I never get any further if I reboot no operating system is found.

What do I do next?

Wayne Phillips
Boulder

---

### Post by jimv on 2009-01-23
Before you select Install on the boot menu, there's a spot where you can type in boot options.  Type acpi=off in there and see if that helps.

---

### Post by chaotos on 2009-01-23
Thanks for the quick response.

I remove the quitet switch and added acpi=off. Following the battery message I now get:

"ubuntu 2.6.27.7 blah blah NO WARRANTY blah blah To use a command as administrator use sudo"

Then I get dropped at the $~ prompt. However the screen flashes intermittentlty. On an attempt to reboot I get a "Disk Boot Failure" message.

PS The system is running XP fine. I switched out the boot drive to try installing Ubuntu.

Wayne

---

### Post by jimv on 2009-01-24
Are you using the Desktop CD or the Alternate CD?

---

### Post by chaotos on 2009-01-24
I was using the default download settings for 8.10 from the Ubuntu site.

This gives me an idea. I am going to try downloading the 64 bit version ... missed the checkbox.

Wayne

---

### Post by chaotos on 2009-01-24
OK I think I was using the desktop CD. I just downloaded the 64 bit version and tried again just to be sure that's what I had. Same result.

Here is some more info: When I first start the Ubuntu CD I get a message "Your BIOS doesn't have an aperature memory hole. Enable IOMMU." I don't know what that means. I did go in and reset my Frame Buffer Size to and Current UMA Size to "Auto" (they had been at 250 and 250 respectively). That didn't help.

Thanks for your suggestions ... please keep them comming. This is not a wierd system and I should be able to get it to work.

Wayne

---

### Post by etdsbastar on 2009-01-24
Please tell me the installation procedure you are performing.


Normal/Full Installation or
Installation under windows...

Tell me clearly what is happening and try to note all the error messages you are getting and then reply here...

...

---

### Post by chaotos on 2009-01-24
OK, let me summarize.

I am doing a full/normal installation of Ubuntu 8.10 64 bit onto a 320 GB unpartitioned drive, using guided installation “use whole drive”. I have also tried pre-partitioning the drive with gparted to no avail.

As mentioned my system consists of a Gigabyte GA-MA69G-S3H motherboard with a AMD Athlon 64x2 4400 Brisbane 2.3 GHz processor. I am using the onboard video with no video card. ;This is a very stable Windows XP computer. For safety I am unplugging the windows boot drive and all other drives prior to trying to install Ubuntu on the fresh drive. Note that I can boot from the Ubuntu Live CD and bring up a Ubuntu desktop without difficulty. I have tried both selecting “install Ubuntu” or “try out Ubuntu, installing from the Ubuntu Live desktop. I have also tried two different monitors. Makes no difference.

Very soon after beginning the installation I see “"Your BIOS doesn't have an aperature memory hole. Enable IOMMU."  I presume this is related to the absence of a video card.

The installation proceeds normally until I see "scanning the mirror." The installation screen fades to black. Then I see several text linex ending with "checking battery state". Then an error message "The display server has shut down 6 times in the last 90 seconds. It is likely something bad is going on." After this the system reboots and cycles through the same process.

Following someone's suggestion, I tried I going into boot options, removing the quiet switch and adding acpi=off. Things proceed as above except I am in verbose mode. Following the same battery message I now get "ubuntu 2.6.27.7 blah blah NO WARRANTY blah blah. To use a command as administrator use sudo" Then I get dropped at the $~ prompt. However the screen flashes intermittentlty. On an attempt to reboot I get a "Disk Boot Failure" message.

I ordered a $25 video card to see if it might work around the problem. But I would appreciate any suggestions you might have.

Wayne Phillips
Boulder, Colorado

---

