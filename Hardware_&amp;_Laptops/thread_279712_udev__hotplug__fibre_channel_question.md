---
title: "udev / hotplug / fibre channel question"
date: 2006-10-18
forum: Hardware &amp; Laptops
---

### Post by RicochetPeter on 2006-10-18
Hi folks,

I just installed 6.06.1-server on a Server. It has an LSI929x type fibre channel controller, and attached devices (on a SAN, f.e.) are detected alright. Here's my question:

How can I make the scsi subsystem detect new LUNs? Like, if I create a new device on the SAN and map it to a LUN so that the machine can see it, I'd actually expect udev to automatically detect the change and create the relevant files, just like it does at boot time. It would also be okay to have a tool to evoke an "SCSI scan" or the likes. Background for this request: The machine will host several virtual machines, and rebooting for adding new disks is not really acceptable :)

I've been searching for two whole days now, all I found is an echo command, which outputs an error.
```
echo "scsi scan-new-devices" > /proc/scsi/scsi
```
gives me 
```
-bash: echo: write error: Invalid argument
```
which obviously means, that this works only in certain other kernel versions, not in mine.

Can anyone please shed some light on this?

---

### Post by RicochetPeter on 2006-11-23
Hi again, too bad nobody seems to have an answer to this question...

The only choices I found are not usable:
- rebooting
- unloading/reloading the driver (if it's a module)

Anyone? Please?

---

### Post by Brazen on 2008-04-28
I know I'm resurrecting a rediculously old thread here, but I've wracked my brain over this off and on for the last couple months and finally found something that works.  This works on my RHEL 5.0 box:
# echo "- - -" > /sys/class/scsi_host/host0/scan

The command must be run as root (this may be different for Ubuntu) and not with sudo.  I get a permission denied with sudo and have to switch to the actually root account with "sudo su -" to run it successfully.  "cat /proc/scsi/scsi" verifies that the new drive shows up.

This is where I found the solution, and there is more information there:
[http://www-941.ibm.com/collaboration/wiki/pages/viewpage.action?pageId=3625](http://www-941.ibm.com/collaboration/wiki/pages/viewpage.action?pageId=3625)

I thought I would post it here, in case anyone else is googling around and comes across this thread.

---

### Post by RicochetPeter on 2008-04-28
Thanks for your reply, Brazen - even if it's late: I don't work with the company I used to back then :) So, too bad, I don't have a system on my hands to check it out.

Thanks also for including the link to the IBM thread, too, not many people answer in such a manner. ;)

---

### Post by Brazen on 2008-04-29
Wow, I'm surprised you responded back.  Considering you have 7 posts to your name and that thread was from a year and a half ago... I figured you just popped into the forum for test drive and had probably long since moved on...

Anyway, I've seen the question come up a few times without ever being answered and I myself came across the situation where rescanning without rebooting would be a huge benefit, so I though I would throw that solution out there.  I worked great for me on RHEL 5.0 though I prefer Ubuntu that just happens to be what the distro on that server, but I bet it would work on any distro with a 2.6 kernel.

---

### Post by Ng Oon-Ee on 2008-06-29
To add a bit more to that, its not really necessary to be logged in as root, you can pipe the echo using tee. I don't know what that means, but I read about it from this thread:-

[http://ubuntuforums.org/showthread.php?t=412329]("http://ubuntuforums.org/showthread.php?t=412329")

For those who don't want to follow the link, the command would look like this:-

```
echo "- - -" | sudo tee -a /sys/class/scsi_host/host0/scan
```

Been looking for a way to rescan the SCSI bus, this thread was very helpful in that regard. Thanks =)

EDIT: copied the wrong command :oops:

---

