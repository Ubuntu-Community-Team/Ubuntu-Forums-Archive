---
title: "Upgrade Xperia to Android 2.1"
date: 2010-11-06
forum: Hardware
---

### Post by jakslev on 2010-11-06
Hi All, 

After the much awaited Android upgrade to 2.1 on the Sony Ericsson Xperia phones was released - I am anxiously waiting to hear if anyone can advise a way of performing this update under Ubuntu or and other GUN/Linux system. 

The upgrade from Android 1.6 to 2.1 requires the use of Sony Ericsson PC Companion, which doesn't work under WINE and doesn't find the USB drive under Virtualbox :(

As with TomTom - it seems that Sony Ericsson just doesn't get that they owe the open source community something that works with our OS !! If not - tey might as well make their systems be Windoze crap!

Any takers?

---

### Post by schmy on 2010-11-07
I find it ironic that a phone built using Android, which itself is a Linux derivative, cannot connect effectively to a Linux system.

I think I may need to hassle a windozing friend into letting me use their system long enough for the upgrade. That is, if I ever get confirmation from my service provider that the upgrade is available (even though they are already using a screencap of the 2.1 software to advertise the model).

*Sigh* There are just so many minor frustrations with this. 

I'll let you know if I find anything else that works.

---

### Post by jakslev on 2010-11-08
Yes - completely agree! 

TomTom does the exact same thing - but I hope some hacker will be able to make a simple walk-through before I bite in the "sour apple" and install Windoze for that specific task...

Besides - reading the specs it doesn't exactly seem that I am missing anything on this great phone! If you havent already you need to install ADW Launcher and get the Ubuntu theme installed :) 

jakslev

---

### Post by Tokyo_Joe on 2010-11-21
I took mine down to the local Docomo shop (mobile phone company) and they had a big set of netbooks on standby labelled "Xperia upgrade for dumb asses without computers" (or pehaps it wasn't that specific). I explained to the happy smiling staff that 'Windows' isn't a computer, they didn't understand, but they did upgrade my phone for me.

---

### Post by jakslev on 2010-11-22
Haha TokyoJoe - I did the same thing at an internetcafe. Felt very unpujre but i did 3 factory resets of the phone after the upgrade to clean out the windows stink :D

Still a shame they dont support Linux better..

jakslev

---

### Post by Fafler on 2010-11-22
Virtualbox and Windows XP. I have one with upgrade software for all kind of phones. A pretty handy tool.

---

### Post by jakslev on 2010-11-22
Hi Fafler, 

Couldn't get that to work on Virtualbox - are you on the paid version of Virtualbox? I believe the free version does not support USB connections..?

If you have a solution to doing it with Virtualbox - do let us know! :o)

Cheers, 

jakslev

---

### Post by Fafler on 2010-11-22
I use the Oracle version of VirtualBox. It's free as in beer, not speech. Make a USB device filter, that allows all USB devices to connect. Nokia phones, at least, change ID's when entering the boot loader mode so this is needed to make sure the upgrade software and phone doesn't loose the connection to each other.

---

### Post by jakslev on 2010-11-23
Okay - might play around with that. Though I tried doing just that on version Virtualbox 3.2.8 (Oracle).  

If you know a way to connect the Sony Ericsson PC Companion and the TomTom Home software via USB using the Virtualbox - I am sure you would become a very popular man :D

Rather free beer than free speech... or wait... yeah eff it just give me a pint!

jakslev

---

### Post by Fafler on 2010-11-23
I don't have a SE phone with android around, but i can do some testing with a HTC phone later. If i get around to do it, i'll post some feedback.

---

### Post by beep_gr on 2010-11-23
> **jakslev said:**
> Hi All, 

After the much awaited Android upgrade to 2.1 on the Sony Ericsson Xperia phones was released - I am anxiously waiting to hear if anyone can advise a way of performing this update under Ubuntu or and other GUN/Linux system. 

The upgrade from Android 1.6 to 2.1 requires the use of Sony Ericsson PC Companion, which doesn't work under WINE and doesn't find the USB drive under Virtualbox :(

As with TomTom - it seems that Sony Ericsson just doesn't get that they owe the open source community something that works with our OS !! If not - tey might as well make their systems be Windoze crap!

Any takers?

The SE update software is based in java scripts... If you install it via wine, you'll see that it uses java. The problem is that I didn't find a way to run the java file separated from the .exe file. 
I need some time, maybe .ini file give us a walkthrough...

---

### Post by Vexiphne on 2010-12-14
> **jakslev said:**
> Hi All, 

After the much awaited Android upgrade to 2.1 on the Sony Ericsson Xperia phones was released - I am anxiously waiting to hear if anyone can advise a way of performing this update under Ubuntu or and other GUN/Linux system. 

The upgrade from Android 1.6 to 2.1 requires the use of Sony Ericsson PC Companion, which doesn't work under WINE and doesn't find the USB drive under Virtualbox :(

Any takers?

You can find a tutorial on how to connect to USB in VirtualBox here: 
[http://hannacam.net/tutorials/ubuntu/how-to-install-sony-ericsson-pc-companion-on-ubuntu-10-10/]("http://hannacam.net/tutorials/ubuntu/how-to-install-sony-ericsson-pc-companion-on-ubuntu-10-10/")

---

### Post by jakslev on 2010-12-15
> **beep_gr said:**
> The SE update software is based in java scripts... If you install it via wine, you'll see that it uses java. The problem is that I didn't find a way to run the java file separated from the .exe file. 
I need some time, maybe .ini file give us a walkthrough...

Yes.. I gave up and simply went to an internet café and did the upgrade :s
Still annoying that companies like Sony Ericsson and TomTom, that utilises the Linux platform - doesn't support us better.

---

### Post by PsynoKhi0 on 2010-12-30
Fresh X8 user here, loving the phone, not so much the "Windows requirement".

I'm seeing the whole issue from a different perspective though.

Although I do have access to computers that would allow me to perform the upgrade to 2.1, I'm holding back for now.

My current programming skills are lousy at best - so I can't contribute to GNU/Linux with code yet.
There is still a lot for me to learn about the technical aspects of the operating system - so I can't contribute with lots of in-depth documentation yet.
Until now I've tried many different distributions, and still distro-hopping quite a lot - so I can't contribute by devoting my time to one particular community yet.

If there is **ONE** way I can contribute, here and now, as an average user, is by letting IT companies know I want them to support my operating system. Just like you can ;)

If I have to be patient and wait a bit so that **in the long run** GNU/Linux gains better support, then I'll wait. Plus the phone is nice as it is with Android 1.6

For every user that gives in to the "Windows only" requirement, that one less reason for manufacturers to support anything else. And I think that's really a shame.

Of course one single voice doesn't weigh much, so I'd like to know if more of you share the same ideas.
Whether it is a fully fledged GNU/Linux compatible PC Companion, source code, or a WINE-friendly version, personally I don't care much. Anything that doesn't require a Windows license in any shape or form will do.
The key is having enough people letting Sony Ericsson know that have customers who aren't bound to Microsoft.

Who's with me? :D

---

### Post by dominoes20 on 2011-01-06
I'm in agreement with you about not giving in to windows only software but I have to strongly disagree with you regarding the differences between 1.6 and 2.1.
When you upgrade, you will notice an increase in battery life, and a noticeable increase in functionality. (Smoother scrolling, better pictures, etc.)
Also, the Android market opens up to you with far more applications available for 2.1. Definitely worth the upgrade.
Can't wait for multi touch and hopefully 2.2

---

### Post by PsynoKhi0 on 2011-01-14
> **dominoes20 said:**
> I'm in agreement with you about not giving in to windows only software but I have to strongly disagree with you regarding the differences between 1.6 and 2.1.
When you upgrade, you will notice an increase in battery life, and a noticeable increase in functionality. (Smoother scrolling, better pictures, etc.)
Also, the Android market opens up to you with far more applications available for 2.1. Definitely worth the upgrade.
Can't wait for multi touch and hopefully 2.2

Those are improvements, and while they are indeed nice, 1.6 still gives you a functional phone :)

---

### Post by PsynoKhi0 on 2011-01-14
> **dominoes20 said:**
> I'm in agreement with you about not giving in to windows only software but I have to strongly disagree with you regarding the differences between 1.6 and 2.1.
When you upgrade, you will notice an increase in battery life, and a noticeable increase in functionality. (Smoother scrolling, better pictures, etc.)
Also, the Android market opens up to you with far more applications available for 2.1. Definitely worth the upgrade.
Can't wait for multi touch and hopefully 2.2

Those are improvements, and while they are indeed nice, 1.6 still gives you a functional phone :)

---

### Post by PsynoKhi0 on 2011-01-14
> **dominoes20 said:**
> I'm in agreement with you about not giving in to windows only software but I have to strongly disagree with you regarding the differences between 1.6 and 2.1.
When you upgrade, you will notice an increase in battery life, and a noticeable increase in functionality. (Smoother scrolling, better pictures, etc.)
Also, the Android market opens up to you with far more applications available for 2.1. Definitely worth the upgrade.
Can't wait for multi touch and hopefully 2.2

Those are improvements, and while they are indeed nice, 1.6 still gives you a functional phone :)

---

### Post by PsynoKhi0 on 2011-01-14
Edit: Sorry double post, for some reason it took a while for the reply to appear.

Anyway, some further thoughts on 1.6 and 2.1, I think 1.6 gives users what they **need**, while 2.1 might give them something they **want**.
So again, I wish people held to 1.6 while asking Sony Ericsson to support other OSes.

---

### Post by PsynoKhi0 on 2011-01-19
Here's an example of what anyone could do, in 10 minutes top :D

[Go to Sony Ericsson's support page]("http://www.sonyericsson.com/cws/common/contact?cc=gb&lc=en") (URL is to the UK page). There are links to a live chat and to the Xperia email support.

Enough people asking (and really, asking, rather than demanding) for a - hopefully mono-free - Linux friendly PC Companion should make them think again :) The source code under the GPL would just be gravy :D

---

### Post by jakslev on 2011-01-21
> **PsynoKhi0 said:**
> Here's an example of what anyone could do, in 10 minutes top :D

[Go to Sony Ericsson's support page]("http://www.sonyericsson.com/cws/common/contact?cc=gb&lc=en") (URL is to the UK page). There are links to a live chat and to the Xperia email support.

Enough people asking (and really, asking, rather than demanding) for a - hopefully mono-free - Linux friendly PC Companion should make them think again :) The source code under the GPL would just be gravy :D

I agree - just entered their website and asked for it :)
In the meantime - I feel pure enough having used a Windoze computer updating from 1.6 - 2.1. Afterall now again my Android needn't have contact with evil Windoze machines (and I have done several master resets) :o)

Here is what I sent them to their UK websites xperia address (find it in PsyonoKhi0's link above):

Dear Sony Ericsson,

Having almost exclusively used your mobile phones since the beginning of the mobile phone age; and being very satisfied with the unparalleled build quality; it was natural for me to chose a smart phone from the the Sony Ericsson Xperia series. However, I have run into a problem - that I hope you will be able to help me with.

Your PC Companion software does not run on Linux, which means I am unable to update from 1.6 -> 2.1 on the Android OS. Can you please advise of a way to perform this update?

If you consider that it would be too costly to support a Linux PC Companion distribution, you might consider releasing the source code to the PC Companion under GPL and letting the open source community maintain a functioning distribution. The notion that your PC Companion should be so business central for you, or include code that is extremely secret and would render Sony Ericsson group uncompetitive is very unlikely.

On the other hand, having embraced the Linux based Android system; you might pay your moral dues to the open source movement you are benefiting from by either giving us access to the PC Companion source code or starting to support a Linux version. If you do not, you are in risk of getting a negative spin going towards your group and making your loyal Sony Ericsson users start opening their eyes to HTC.

While Linux users are still a small group (though the fastest growing one), we are somewhat peculiar in that many of us function as support and computer geeks for other people. In other words, people come to us to ask for advise on a very personal IT-level.
Keep us happy and super-satisfied with your products, please :o)

Best Regards,

---

### Post by francois.harmse@gmail.com on 2011-03-10
> **PsynoKhi0 said:**
> Fresh X8 user here, loving the phone, not so much the "Windows requirement".

I'm seeing the whole issue from a different perspective though.

Although I do have access to computers that would allow me to perform the upgrade to 2.1, I'm holding back for now.

My current programming skills are lousy at best - so I can't contribute to GNU/Linux with code yet.
There is still a lot for me to learn about the technical aspects of the operating system - so I can't contribute with lots of in-depth documentation yet.
Until now I've tried many different distributions, and still distro-hopping quite a lot - so I can't contribute by devoting my time to one particular community yet.

If there is **ONE** way I can contribute, here and now, as an average user, is by letting IT companies know I want them to support my operating system. Just like you can ;)

If I have to be patient and wait a bit so that **in the long run** GNU/Linux gains better support, then I'll wait. Plus the phone is nice as it is with Android 1.6

For every user that gives in to the "Windows only" requirement, that one less reason for manufacturers to support anything else. And I think that's really a shame.

Of course one single voice doesn't weigh much, so I'd like to know if more of you share the same ideas.
Whether it is a fully fledged GNU/Linux compatible PC Companion, source code, or a WINE-friendly version, personally I don't care much. Anything that doesn't require a Windows license in any shape or form will do.
The key is having enough people letting Sony Ericsson know that have customers who aren't bound to Microsoft.

Who's with me? :D
no luck from my side though, after a chat with SE support this was the feedback - 
Please wait while we find an agent to assist you...
You have now been connected to an agent.
Gaynor:  Thank you for contacting Sony Ericsson UK Chat Support. My name is Gaynor, how can I help you today?
francois:  hi there, I am Francois,
francois:  I have have a x10 mini pro and would like to update my phone via linux
francois:  i can not pay 200pounds for an OS just to update a phone!
francois:  are there any solutions for performing this via Linux?
Gaynor:  Unfortunately, it is not possilbe to update your handset using linux. Do you not have access to a windows pc at all? If not you can send your phone in for service and we would flash it there for you
francois:  i can do that, but this is quite embarrassing as the phone seems to be a great opensource supporting step forward making use of a linux kernel, and then one needs windows to support the linux based phone.
francois:  can i please request SE look at producing a solution for this? support on linux?
francois:  there are huge linux communities out there in the same boat as I...
francois:  my next phone would have been SE xperia arc, but rather considers going for samsung or alternative because of this.
Gaynor:  We can't support a Linux based OS due to the many distributions that are available, from a support perspective as the OS is so customisable it would be very difficult to support users.
francois:  WOW! I will certainly post your (SE's response) to the linux community. Linux for one is linux for all!!! You do it for one and it WILL (guaranteed) work for the rest!!!

---

### Post by francois.harmse@gmail.com on 2011-03-10
this was official SE reply - so i will rather upgrade to samsung / htc / motorola - who else does android-linux phones?

---

### Post by jakslev on 2011-03-11
Yes - very sad. Problem is they think that they would have to support the pc companion application in the old proprietary way, without realizing that it would be self-maintained from the community. 

As I mentioned I upgraded my phone in a dirty sleazy internet café using some virus infested Windoze box. After that I cleaned and scrubbed. 

I would consider doing the same if I were you - we can't control the processes behind building our products (yet) - I'm sure my car and TV and other goods are also impure in relation to open source. 

Thanks for the feedback!

---

### Post by PsynoKhi0 on 2011-04-06
> **francois.harmse@gmail.com said:**
> this was official SE reply - so i will rather upgrade to samsung / htc / motorola - who else does android-linux phones?

Thanks for taking the time to contact them!
Although I understand the frustration - since I share it - you displayed in the last line during that chat session, I think it's better to keep one's cool no matter how silly their answer is.
And judging from the excuse the employee gave you, I suppose they had little clue about what they were talking about.
On the other hand, it gives us material to, little by little, debunk their pre-made answers.
So about his one - i.e. too many distributions - from the top of my head:
1. That's what libraries and source code are for
2. They can release static versions - other software vendors do just fine
3. They can work more closely with Wine devs should they wish not to release a GNU/Linux-specific version
4. They can limit their support to the top 10 according to Distrowatch (though it would be unfair for others, so more like a last resort)

At any rate, please keep 'em comin'... We'll show them :D

---

### Post by PsynoKhi0 on 2011-05-11
Well there is some hope! (Even if it's quite involved at this point, and more geared towards developers)
[http://blogs.sonyericsson.com/developerworld/2011/05/06/how-to-build-a-linux-kernel/]("http://blogs.sonyericsson.com/developerworld/2011/05/06/how-to-build-a-linux-kernel/")

---

