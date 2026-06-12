---
title: "android programming on ubuntu"
date: 2009-08-09
forum: Installation &amp; Upgrades
---

### Post by mahdi68 on 2009-08-09
Hi , i want to learn programming for android , so i download android sdk 1.5 and netbeans plugin . i have a problem when i run program that i Have written emulator not shown !!! and this message shown : select device
please help me , what i should do ???

---

### Post by phillw on 2009-08-09
> **mahdi68 said:**
> Hi , i want to learn programming for android , so i download android sdk 1.5 and netbeans plugin . i have a problem when i run program that i Have written emulator not shown !!! and this message shown : select device
please help me , what i should do ???


Try this guys solution ...

[http://ubuntu-unleashed.com/2008/10/howto-run-google-android-on-ubuntu.html](http://ubuntu-unleashed.com/2008/10/howto-run-google-android-on-ubuntu.html)

Hope it is of help.

Regards,

Phill.

---

### Post by jordilin on 2009-08-09
> **mahdi68 said:**
> Hi , i want to learn programming for android , so i download android sdk 1.5 and netbeans plugin . i have a problem when i run program that i Have written emulator not shown !!! and this message shown : select device
please help me , what i should do ???

Have you created an Android Virtual Device?:
```
android create avd --target 2 --name my_avd

```

---

### Post by mahdi68 on 2009-08-10
> Try this guys solution ...

[http://ubuntu-unleashed.com/2008/10/...on-ubuntu.html](http://ubuntu-unleashed.com/2008/10/...on-ubuntu.html)

Hope it is of help.

i download andorid-sdk-linux_x86-1.5_r3 and extract it ,then cd to tools in the android directory then double click on emulator but absolutely nothing happen !!! 
> Have you created an Android Virtual Device?:
Code:

android create avd --target 2 --name my_avd


i try this cod but its not work !!!

---

### Post by mahdi68 on 2009-08-10
how can i create android virtual device ???

---

### Post by phillw on 2009-08-10
I'll give the instructions in the article i posted a try myself ...

Give me a little while.

Regards,
Phill.

---

### Post by phillw on 2009-08-10
<< Back

Well, this is what I did ... Followed the instructions with the exception of emulator - as, like you, it did not do anything !!!

I followed the instructions here .... to get the package..

[http://developer.android.com/sdk/1.5_r3/index.html](http://developer.android.com/sdk/1.5_r3/index.html)

Then followed the instructions here .....

[http://developer.android.com/sdk/1.5_r3/installing.html](http://developer.android.com/sdk/1.5_r3/installing.html)

- I downloaded Eclipse... I kept notes of what went on, I post them below ..

```

did the apt-get for the sun engine

Already have it.

Got and uncompressed the android-sdk... (onto my desktop, so I can find it !)

Downloaded eclipse-java-galileo ...  My system used archive manager, I unzipped, again to desktop

Ran Eclipse - set it to the default directory (~home/phillw/workspace)

My version shows as
/galileo/eclipse//plugins/org.eclipse.platform_3.3.200.v200906111540/splash.bmp
-launcher

(v3.3)

Although, when adding the ADT plug-in, it appears I have v3.4 !!

Next, installed the ADT plug-in as per instructions for v3.4 (Ganymede)

After a few moments, "Developer Tools" appears, put tick in box, then the Next> button.

Next>, again, accept the terms & conditions

Finish.

Now, it's away doing an install (It's gr8 fun, this.... It better not hurt my installation !!!)

Restarted eclipse..

Windows, Preferences ...

Select Android on left ...

Browse to SDK directory...

Click OK ... wait a minute & 3 Target names appear

Click 'OK' ...

And, with no errors reported, according to the installation instructions, it's running !!!



```Hope the above is of help.

Regards,

Phill.

P.S.  While having a play ...I worked out that under the windows menu you have the android AVD Manager .. You can go and create a choice, in my case, of three types
with 2 sizes of SD card.

---

### Post by mahdi68 on 2009-08-10
tanks a lot :P

---

### Post by syed.rakib.al.hasan on 2010-05-17
i am having some problems starting the AVD.

my android virtual device shows up when the AVD is hit to start. but it doesnt show up properly.
~ i am using android 2.1 API-7.
~ i am using linux ubuntu 9.10 karmic
~ i am using eclipse 3.5

[COLOR=Red]_**the problems is**_[/COLOR]

upon setting up the AVD from AVD Manager in eclipse - the defaul skin HVGA cannot be used. it says **"Skin HVGA does not exist"**

[COLOR=Green][B]please help.....
please help.....
please help.....

screenshot for the NO HVGA skin problem
[IMG]http://i.imgur.com/NX5Vs.png[/IMG]




[/B][/COLOR]

---

