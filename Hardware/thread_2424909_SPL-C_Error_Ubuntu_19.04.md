---
title: "SPL-C Error Ubuntu 19.04"
date: 2019-08-17
forum: Hardware
---

### Post by MrRubik on 2019-08-17
Hello. I am a new Ubuntu user and I've finally got most of the things I need to figured out EXCEPT for my Samsung C410w printer. I have followed all the proper procedures including installing the Unified Linux Driver and correctly configuring the printer in Ubuntu. However, every single time I try to print (test page or regular print) I am getting an SPL-C Error. The list of the errors I've gotten are below. I have spent about 6 hours tonight trying to nail this down and I have gotten absolutely nowhere. I have read that this problem did not exist in 18.04 and is specific to 19.04 and a few other distros. This printer is apparently not very popular with Linux users, but it's an expensive color laser printer and I really need to get it to work as it's my only printer and school is starting back in a week. If anyone can help me with this, words can't express how much I would appreciate it.

SPL-C Error - FALSE
SPL-C Error - Disconnected from Host
SPL-C Error - Insufficient Memory

Things I've Tried
1 - IPP, AppSocket/HPDirect, LPD
2 - ~30 Uninstalls and Reinstalls
3 -  Multiple Driver Versions

---

### Post by Autodave on 2019-08-17
Print Driver (Driver) ver.V1.00.36_00.91 for Linux.  Is that what you installed?  That is the only one that I see that is for Linux.

As for 19.04, personally I would go back to 18.04.  18.04 is a long term service release (LTS).  The next LTS will be 20.04.  (The 18 stands for the year and the 04 for the month.)  The LTS releases are supported for at least 5 years, the others only for 9 months.  The LTS releases are very stable, the others not so much.  I like to think of the interim releases as beta releases: new things are being tried, some work, some don't.

---

### Post by MrRubik on 2019-08-18
I installed the latest driver, which is 1.00.39. I have scoured the internet but have not found a solution, but I have discovered an excellent workaround. For those of you that have a Samsung Xpress SL-C410w or similar, your printer has built-in Google Cloud Printing and Samsung Cloud printing. I just registered my printer as a Google Cloud printer and then when I go to print it shows the option to print to my C410w via Google Cloud Print. No drivers required and no hassle. For this to work, you do need to be signed into your Google account through Ubuntu. Really hoping this helps someone.

---

### Post by brian_p on 2019-08-18
> **baileyhood said:**
> I installed the latest driver, which is 1.00.39. I have scoured the internet but have not found a solution, but I have discovered an excellent workaround. For those of you that have a Samsung Xpress SL-C410w or similar, your printer has built-in Google Cloud Printing and Samsung Cloud printing. I just registered my printer as a Google Cloud printer and then when I go to print it shows the option to print to my C410w via Google Cloud Print. No drivers required and no hassle. For this to work, you do need to be signed into your Google account through Ubuntu. Really hoping this helps someone.

That's a really well-thought out solution. I wonder if it might lead to a solution which does not involve Google. What do you get for

```
avahi-browse -rt _ipp._tcp
```

---

### Post by MrRubik on 2019-09-29
> **brian_p said:**
> That's a really well-thought out solution. I wonder if it might lead to a solution which does not involve Google. What do you get for

```
avahi-browse -rt _ipp._tcp
```

Brian,

For some reason, I did not get a notification when you responded to my thread. So, I never got a chance to run that command because I have now upgraded to the Ubuntu 19.10 Beta. The issues with the Samsung C410w printer have been worked out. Everything is working great. Hope this helps someone else who was having printer issues!

---

### Post by brian_p on 2019-09-29
> **MrRubik said:**
> Brian,

For some reason, I did not get a notification when you responded to my thread. So, I never got a chance to run that command because I have now upgraded to the Ubuntu 19.10 Beta. The issues with the Samsung C410w printer have been worked out. Everything is working great. Hope this helps someone else who was having printer issues!

Glad you have sorted out your problems. The output of ```
avahi-browse -rt _ipp._tcp
``` would still be useful to have in my records.

---

