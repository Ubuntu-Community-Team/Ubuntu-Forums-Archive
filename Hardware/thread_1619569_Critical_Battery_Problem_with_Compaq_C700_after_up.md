---
title: "Critical Battery Problem with Compaq C700 after upgrading to 10.10"
date: 2010-11-11
forum: Hardware
---

### Post by tim89 on 2010-11-11
Hello,

I have been using a Compaq C700 laptop using Ubuntu 8.10 for years.

Two days ago I wiped the hard drive and started again by installing Ubuntu 10.10.

Since upgrading I have had major problems with the power management that render this laptop useless as a laptop.

1. When power is unplugged I get a critical low battery warning (even though the battery is fully charged) and it suspends or hibernates.

This means I always have to use the battery plugged into the mains.

This was not an issue under ubuntu 8.10.

Is there a way I can turn the power management off in ubuntu? I dont really care about battery read outs or if the machine suddenly switches off.

Thanks

Tim

---

### Post by animeshmeher on 2010-11-12
Hi! [tim89]("http://ubuntu-ky.ubuntuforums.org/member.php?u=635320")
Try this, 
Press Alt-F2 and type **gconf-editor**. Press Enter. 
Navigate to **Apps -> gnome-power-manager -> general**. 
**De-select** the option **use_time_for 1f40 _policy**.

No need to restart, just close the config editor.

That should help. 

I suggestion though. Please google your problem a bit before posting . Thatll save duplicate post. :-)
Even i had the same problem and googled for the answer.

---

### Post by tim89 on 2010-11-15
Hello,

Thanks for the reply. I have applied the fix and will see if it worked!

For your information I DID Google this quite extensively but found nothing.

Luckily you did and you helped me out so thanks!!!

Tim

---

### Post by ether3al on 2010-11-28
Tim89 when your laptop powered down, would it turn back on?

I am experiencing a similar issue however as I have hibernate etc disabled my laptop simply powers off and will not turn back on until I plug it in. Just hoping that it is similar to yours and not hardware related.

---

