---
title: "Ati Radeon card not working after upgrade"
date: 2009-02-11
forum: Installation &amp; Upgrades
---

### Post by tommalley on 2009-02-11
Guess the title says it all

Have looked at the xcon file and card is showing. Cannot find restricted drivers manager on Heron.

Thinking that the confilciting driver is also the reason that heron is now hanging at splash screen. Have removed the splash screed and it just hangs on waiting for root file system.

If I can get past a couple of issues here there is another ubuntu convert in the making.

help really appreciated all.

---

### Post by travisman26 on 2009-02-11
deactivate the old drivers do that by going to system<>administrator<>hardware drivers after the ati graphics card drivers r disabled go to ati website and go to driver area and click linux under the selection then click radeon then click the graphic card u have if you dont know what graphics card you have go to applications<>accessories<>terminal and type lspci | grep VGA you should get a message back saying something similar to this 01:05.0 VGA compatible controller: ATI Technologies Inc RS780MC [Radeon HD 3100 Graphics]
just look at the end were it says [radeon hd 3100 graphics] just use whatever your output says it is probably gona be something different once you select your graphics card on the ati driver section on there website click go and it will take you to the next page and on that page click the download driver link and download it to your desktop IF IT IS A TAR.GZ or something ziped just tight click and go to extract if its not ziped dont worry about it rename the file to ati.run insted of the long name it will make it easy, now in the terminal type sudo su and type your password now type sh ati.run and a gui will come up and just follow through that and restart your computer and it will work.  the reason why we changed name of the .run file is beacuz if we didnt you would have to type in sh then that entire name

---

### Post by tommalley on 2009-02-11
Hi,
thanks for your answer. the problem is when i go to hardware drivers there is nothing to click on. the card is a rv100

If I follow the rest of the steps will it work or is there something else wrong?

---

### Post by the.scarecrow on 2009-02-11
Hi

I found this link very helpful when I setup my ATI Radion 9000 in Hardy 8.04. I had to use the open source drivers and they work just fine. Hope this helps you too.

[HTML]https://help.ubuntu.com/community/RadeonDriver
[/HTML]

---

