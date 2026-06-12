---
title: "Installing the 3.4.4. kernel onto my T430s."
date: 2012-07-01
forum: Hardware
---

### Post by Zenoctilles on 2012-07-01
My T430s, on the current installation of 12.04, would occasionally hang. This is a machine loaded with the latest Ivy Bridge processor. I read that installing a more recent kernel helps to mitigate these system hangs. 

But, the question remains: How do I do it?

---

### Post by DTedesco on 2012-07-08
I also have the T430s. It has already freezed twice in the first week ...
Where did you read about those issues related to Ivy Bridge?

---

### Post by Redblade20XX on 2012-07-08
If you want, you can download the kernel files from the main kernel repositories, compile and install it yourself.

See here:
[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)
[http://kernel.org/](http://kernel.org/)

As a note, Ubuntu might not like the raw kernel since Ubuntu takes the raw kernel and does some modifications on it before allowing the user to install it through the package manager.

You can also wait until the kernel is uploaded to the main repositories.

-Red

---

### Post by DTedesco on 2012-07-08
He could also download the .deb-files from here:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.4.4-quantal/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.4.4-quantal/)

---

### Post by Redblade20XX on 2012-07-08
> **DTedesco said:**
> He could also download the .deb-files from here:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.4.4-quantal/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v3.4.4-quantal/")

Did you install it? If so, did it resolve the ivy bridge problems?

-Red

---

### Post by rogerbinns on 2012-07-10
I'm another new T430s user and also experiencing random hangs.  They seem to happen most when there is disk activity.  I was thinking of blaming my new mSata drive, but that seems like a bad candidate now, especially I was experiencing it while moving the mouse.

Here is a posting from someone with a Dell but the same processor and chipset, and showing how they got the 3.4 kernel [http://ubuntuforums.org/showpost.php?p=12035647&postcount=16](http://ubuntuforums.org/showpost.php?p=12035647&postcount=16)

Update: After installing the 3.4 kernel I haven't had a single lockup despite getting them frequently before.

Separately stay away from OCZ Nocti mSata drives.  The quoted specs are after the controller does compression so they can make up whatever numbers they want (eg multiply real performance by 5 assuming a 5:1 compression).  With encrypted data (like you should do on a laptop) there is no compression and the actual base specs are dismal.

---

### Post by wangxiao1254 on 2012-10-01
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.4-precise/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.4-precise/)

There are some deb packages for you to isntall if you want, just dpkg it.

I'm also a t430s user with random hang:-(

---

### Post by yyxxcc on 2012-10-07
The new kernel is great. No freeze or crash so far.


> **rogerbinns said:**
> I'm another new T430s user and also experiencing random hangs.  They seem to happen most when there is disk activity.  I was thinking of blaming my new mSata drive, but that seems like a bad candidate now, especially I was experiencing it while moving the mouse.

Here is a posting from someone with a Dell but the same processor and chipset, and showing how they got the 3.4 kernel [http://ubuntuforums.org/showpost.php?p=12035647&postcount=16](http://ubuntuforums.org/showpost.php?p=12035647&postcount=16)

Update: After installing the 3.4 kernel I haven't had a single lockup despite getting them frequently before.

Separately stay away from OCZ Nocti mSata drives.  The quoted specs are after the controller does compression so they can make up whatever numbers they want (eg multiply real performance by 5 assuming a 5:1 compression).  With encrypted data (like you should do on a laptop) there is no compression and the actual base specs are dismal.

---

### Post by monnand on 2012-11-18
I have a T430s too. I experienced random hangs as well. ** It is not the GNU/Linux's problem, it is the motherboad's problem.** (It is confirmed by Leonovo)

If you bought your T430s before Sep. 7th, then you may got a defective laptop. Updating kernel won't fix the problem --- I tried 3.4.x, 3.6.2 and it failed as well.

For more details on this, here is my thread: [http://ubuntuforums.org/showthread.php?t=2065734](http://ubuntuforums.org/showthread.php?t=2065734)

**The only solution right now is sending your laptop back to lenovo and let them fix it on site.**

Here was what I did:

- Before sending my laptop back, I backed up all my data and used a live CD and executed the following command to erase my hard drive:

```

$ dd if=/dev/zero of=/dev/sda bs=8M

```The command above will erase your whole drive leaving only zero on every byte. The reason I did this: Those people in lenovo will try to find every possible way to not fix your laptop. One possible excuse would be "You installed a Linux, sir. We cannot fix it if you installed an unsupported OS."

- Print this web page: [http://help.wfu.edu/thinkpads/t430s/status](http://help.wfu.edu/thinkpads/t430s/status) with a line in the front: "My laptop has same problem! Change the motherboard." Send the printed web page along with your laptop to Lenovo

- Check your status everyday **by phone**. Otherwise they may forget your problem. If possible, ask the name of the person who was assigned specific to your problem and call him/her everyday to remind him/her your problem. I did this because I cannot access their on-line system (I got HTTP 500 error every time I access it and it is of course their server's problem.) From my experience, even if I called them everyday, it took me 3 weeks to get my laptop back.

---

