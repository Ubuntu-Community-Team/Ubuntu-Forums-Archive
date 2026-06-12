---
title: "Getting a patch applied to a standard driver"
date: 2015-01-24
forum: Hardware
---

### Post by daniel-james-sonadata on 2015-01-24
I have an Ubuntu (actually Mythbuntu, but this question isn't specific to MythTV) box that contains a Avermedia A373 mini-PCIe DVB-T receiver card. This card is based on IT913x chips, but isn't supported by the standard driver in Ubuntu (or Mythbuntu).

When I first got this card, I discovered that there was a patch to add support to the IT913x driver -- nothing fancy, just adding the card's ID so the driver will recognize it -- so I added the patch, and the card worked fine. The patch was pretty new at the time so I expected that it would be merged into the stock driver in the next few release cycles. I don't mind patching a driver myself to get support for something new, but it gets to be a pain if I have to do it every time there's a change in kernel version.

I've recently updated the box to 14.04 (I like to stick with LTS releases for something like this, but the update was overdue) and was disappointed to see that the card is still not supported 'out of the box'.

The patch is this one: [http://www.spinics.net/lists/linux-media/msg50602.html](http://www.spinics.net/lists/linux-media/msg50602.html)

What can I do to push for it to be merged into the standard driver?

---

### Post by weatherman2 on 2015-01-24
If a bug has been filed and fixed, then it's a matter of someone approving a merge into the standard driver.  But that takes work.  The main thing is, the developers need to make sure this patch doesn't break anything else.

Why don't you write a script to install the patch automatically?

First write the script to do it, so you can run the script manually after a kernel update.

Once you get that to work reliably, then put a hook to it in your /etc/rc.local file so at each boot it can check for the need to build it again and do it if need be.  Then it should be largely transparent to you.

---

### Post by daniel-james-sonadata on 2015-02-05
Yes, sure, I can script a rebuild of the driver after a kernel update. That'll be more work for me than building the driver manually a few times, though. I have avoided doing so, so far, because I had thought that the script would only need to be run once or twice before the patch was incorporated into the main driver.

So, let me rephrase the question: Is there anything I can do to help with the process of merging the patch into the driver so that it will be easily accessible by others?

---

### Post by ian-weisser on 2015-02-05
I would politely follow up with Malcolm Priestly, who signed off on the merge, and ask for his advice.

If the patch was in the kernel, but is no longer, then do some git-fu, see if you can find where it was added, see if you can find where it reverted, and file a kernel bug report.

---

