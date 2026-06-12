---
title: "[SOLVED] Last update (2.6.27-11-generic) won't install linux-restricted-modules-gener"
date: 2008-12-19
forum: Installation &amp; Upgrades
---

### Post by Ivo Moelans on 2008-12-19
I did the last automatic (2.6.27-11-generic kernel) update. It warned me that not all upgrades could be executed, but I should upgrade what I could. So I did. Everything seems to be fine, but *linux-restricted-modules-generic* is not updated.
When I try the sudo apt-get update & upgrade thing in the terminal, it says *The following packages have been kept back: linux-restricted-modules-generic*. Basically the same.
Can anybody tell me if I can do something about this, or shouldn't I be worried and will that package be updated later?

---

### Post by cb34 on 2008-12-20
I have the exact same problem here.
exact same messages and everything.

1 package now sitting that wont install no matter what i try.. ????

this last update wasn't normal.. some problem for sure.

EDIT-> oops, i'm rude..hehe.. i meant to say..

can someone please help me and Ivo with this issue.
i have a feeling some crashes might come from this.. maybe.. i hope not. :D

---

### Post by jakala on 2008-12-20
Hello,

I have the same issue, and my wireless network card isn't recognized.

I use an HP Compaq nw8000.

Jakala

---

### Post by lseguin on 2008-12-20
Same issue here since doing a standard update .. won't install restricted modules and wireless not working.

---

### Post by cryptovenom on 2008-12-20
i'm having the same problem also.

---

### Post by schimschone on 2008-12-20
I was in the middle of clearing bloat from my Mini 9, when I forced an update from Synaptic Package Manager, and the new kernel ('2.6.27.11') was installed.. needless to say my Wifi card is no longer recognised and 'linux-restricted-modules-generic' unavailable for download. 

I worked around this by loading the original kernel ('2.6.27.10') from the start-up menu, and then set it as the primary kernel using a terminal and editing GRUB. 

Thankfully I had some help.. thanks Nathan.

Now I'm receiving this update on my primary laptop (Latitude D520), and again 'linux-restricted-modules-generic' is not available for download. 

My concern is that if the new kernel is not ready for prime time then why is it being put out there?

While I'm pretty understanding of these things, I have at least two friends willing to switch from MS to Ubuntu in the coming week.. but if they end up losing internet connectivity when they update, I can already hear them calling me asking to switch back.

As has been stated elsewhere, Wifi support is a necessity for Ubuntu users, and paramount for keeping new users.. but I will keep that as close as I get to ranting, but some prompt support on this issue would be appreciated.

Thank you in advance,

schim

---

### Post by fanie on 2008-12-20
> **cryptovenom said:**
> i'm having the same problem also.

I have the same problem:

It was not possible for to upgrade following packages: linux-backports-modules-intrepid linux-backports-modules-intrepid-generic
  linux-generic linux-headers-generic linux-image-generic
  linux-restricted-modules-generic

I tried to install one for one, starting with linux-image-generic and linux-image-2.6.27-11-generic, then  linux-headers-2.6.27-11 linux-headers-2.6.27-11-generic, linux-headers-generic.

Now linux-backports-modules-intrepid linux-backports-modules-intrepid-generic, linux-restricted-modules-generic are left to be installed.

Apparently linux-backports-modules-intrepid depends on linux-backports-modules-intrepid-generic, which depends on linux-backports-modules-2.6.27-11-generic, doesnt exist. Same for linux-restricted-modules-generic, which depends on linux-restricted-modules-2.6.27-11-generic, doesnt exist either.

This bug is reported all over the web.

Wait 24 hours and report the problems, and i think/ hope, the problem will be solved...

---

### Post by NilsE on 2008-12-20
I got everything installed via the update manager with the exception of the restricted module.  Since these were in the proposed I expect problems so I will wait patiently for the updated restricted.  Typically happens within 24 hours.

---

### Post by cb34 on 2008-12-20
wierd... after doing the same thing a bunch of times..IT NOW WORKED.. IT UPDATED! along with 2 other updtes.. woohoo! im happy.. hehe

i went into UPDATE MANAGER(which i previously did many times over), did CHECK, and the non-selectable package is now selected along with 2 other packages.

it worked.. updated like normal..

try it again everyone.. maybe they just updated something. :D

---

### Post by Ivo Moelans on 2008-12-20
I can confirm what cb34 wrote. Apparently they 'updated the update'. Three restricted module files were installed like normal.
I had to change my server to the Main Server in *System&#8594;Administration&#8594;Software Sources* though. My local server hadn't received the new restricted modules yet.

So, this thread can be marked 'Solved'.

---

### Post by cb34 on 2008-12-20
just a FWIW.. my server has alwayz been set to MAIN.. for months if i choose my local server(Canada), it is SUPER slow.. so i never use my local server even though i know i should. the Canada server is just so slow.

---

### Post by Ivo Moelans on 2008-12-20
My server in Belgium is usually faster than the main server. Which is useful in the periods when a new distribution is issued and the main server sometimes becomes rather slow. On the other side it gets its updates later apparently.

---

### Post by greatst on 2008-12-20
> **Ivo Moelans said:**
> I can confirm what cb34 wrote. Apparently they 'updated the update'. Three restricted module files were installed like normal.
I had to change my server to the Main Server in *System&#8594;Administration&#8594;Software Sources* though. My local server hadn't received the new restricted modules yet.

So, this thread can be marked 'Solved'.

Just to confirm that I understood: You ignored the window warning you that you couldn't install all updates, then you checks the updates that were initially unchecked and the update was performed with no problems? And your system now works correctly?

[offtopic]since this is my first post at this forum, hello to everyone! :guitar:[/offtopic]

---

### Post by cb34 on 2008-12-20
no.. there is no window warning anymore.. it all works like normal as if there was no problem in the first place. go to UPDATE MANAGER, do CHECK, and it should work now.

---

### Post by Ivo Moelans on 2008-12-20
No, I didn't ignore the warning: it isn't there anymore. They fixed it.
Like cb34 said: it should work now.
BTW: everything works as it should, and welcome to the community greatst.

---

### Post by NilsE on 2008-12-20
> **Ivo Moelans said:**
> I can confirm what cb34 wrote. Apparently they 'updated the update'. Three restricted module files were installed like normal.
I had to change my server to the Main Server in *System&#8594;Administration&#8594;Software Sources* though. My local server hadn't received the new restricted modules yet.

So, this thread can be marked 'Solved'.

I was just going to post the same thing.

Side note: I have found that the safest way to do a partial update is with update manager.  Every time I did it with command line or Synaptic it got messed up. Could have just been coincidence.

---

### Post by schimschone on 2008-12-20
Well I can confirm that my Wifi now works, it's still not seeing my ethernet cable at all.. so I cannot confirm that this is [solved].

However I still have full functionality in 2.6.27-10

Has anyone else noticed this?

schim

---

### Post by greatst on 2008-12-20
> **cb34 said:**
> no.. there is no window warning anymore.. it all works like normal as if there was no problem in the first place. go to UPDATE MANAGER, do CHECK, and it should work now.

> **Ivo Moelans said:**
> No, I didn't ignore the warning: it isn't there anymore. They fixed it.
Like cb34 said: it should work now.
BTW: everything works as it should, and welcome to the community greatst.

> **NilsE said:**
> I was just going to post the same thing.

Side note: I have found that the safest way to do a partial update is with update manager.  Every time I did it with command line or Synaptic it got messed up. Could have just been coincidence.

Well, I was using as software source the one for my country (Greece). I changed the setting to "Main Server" and now everything is ok! I suppose that the correction of the problem has not yet propagate to the Greek mirror.

**_edit:_** well, everything seems to go well after the updates. I tried NetBeans, all seems to work properly. I also tried xVM, which worked after first issuing the following command it "asked" me to issue (I added the **sudo** since it didn't execute without it):

```
sudo /etc/init.d/vboxdrv setup
```

---

### Post by schimschone on 2008-12-20
I'm new to using the forums, so I appologize if this is a double post.. but I still can't use my ethernet in conjuntion to the new kernel.

schim

---

### Post by cb34 on 2008-12-20
i would help ya if i could man.. my internet is all workin fine.. i would check all your network settings in the ubuntu menus.. like in admin or preferences somewhere..

also, maybe a reboot will get it going if you didn't already after upgrading. ??

also, you sure your ethernet cable--> router is all workin and lettin traffic through? i dunno really, just some ideas.

---

### Post by Ivo Moelans on 2008-12-20
@Schimschone

I also have no idea what it could be. I have no ethernet and my internet connection is working like it should. But I suggest you start a new thread with something like *"Ethernet doesn't work after latest update"* with as much details as possible. The problem in *this* thread is solved and people who could maybe help you are not likely to read about your ethernet problem.
Good luck.

---

### Post by schimschone on 2008-12-20
Nope, I have no ethernet support under the new kernel (2.6.27-11), however it works fine under the previous version. I have restarted several times, and I have tried reinstalling the new kernel.. still nothing.

Here's my chipset:

Broadcom Corporation BCM4312 802.11b/g (rev 01)
Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev ff)

I'm open to any suggestions.. even the possibility that I missed something.

Thanks a head a time, btw.

schim

---

### Post by adaszek on 2008-12-21
i've got the same problem on my msi wind.

After update to 2.6.27-11 my ethernet connection doesn't work.

---

### Post by schimschone on 2008-12-21
I created a new thread for just the ethernet issue yesterday,:

[http://ubuntuforums.org/showthread.php?t=1017057&highlight=ethernet](http://ubuntuforums.org/showthread.php?t=1017057&highlight=ethernet)

Post something there so they don't think it's me all alone. As for a fix, I just reedited GRUB to automatically load 2.6.27-10 on startup.. I can explain the process if you need.

I plan to run the prior kernel until this one is really truly really ready for primtime.

schim

---

### Post by da_huss on 2009-03-08
I believe my problem fits in this post, as it's that 2.6.27-11 won't properly install.  All my hardware seems to be working fine, and 2.6.27-11 boots up just fine, but as soon as I connect to my network, Update Manager says I have 4 updates to install which just happens to be 2.6.27-11.  I've installed it 3 or 4 times, and I've tried Checking for new updates to see if it disappeared, but it's still there to this day.  I don't know if it's a bug in Update Manager, or what the deal is, but I'd appreciate any help anyone can give me.. thanks.

---

### Post by da_huss on 2009-03-09
Disregard.  I tried again with Synaptic, it installed, I rebooted, and it no longer lists 2.6.27-11 as a possible update.

---

