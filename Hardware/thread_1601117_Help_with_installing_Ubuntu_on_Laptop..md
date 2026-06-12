---
title: "Help with installing Ubuntu on Laptop."
date: 2010-10-19
forum: Hardware
---

### Post by dh390 on 2010-10-19
Hi,
I am new to Linux but I do have some computer knowledge.
 
My problem is I just fixed & put together a laptop & figured I would try out Linux. I downloaded the Ubuntu 64 Bit file image & burned it to a CD-R using Ashampoo Burning Studio. Burned with no problem. 
 
The laptop I am trying this on is a Averatec 7170 with AMD Turion 64 X2 TL-50, 500meg of memory, nVIDIA Geforce 6100 graphics. 
 
I first booted the laptop with the disc. It booted ok. It was slugish & has some issues. So I figured it would run better if I actually installed.
 
Everything was going good. Linux saw both the eithernet port & wireless card as well as the sound card. The problem happened when I got to the screen where you enter your name, computer name, user name & pass words. When it finished loading the drivers & such it would not allow me to go to the next screen. It said it was ready when I was. Well I was ready but it only had the "Back" icon accessible to click on. 
 
Can someone please tell me what I need to do to go to the next screen & finish the install?
 
Thanks.

---

### Post by mikewhatever on 2010-10-19
Make sure your username is alphabetical, without spaces, dots and other special characters. Same for the computer name.

---

### Post by dh390 on 2010-10-20
I know the user name & my name were all letters & no spaces. And I think the computer name had LETTERS & #'s with no spaces. 
 
I will try that.
 
BUT the problem I now have is after the last forced shutdown I had to do my laptop now WON'T turn on. 
 
Is it possible for Ubuntu to corrupt or damage the computers bios?
 
I have removed the batt & power cord, dvd+rw drive, memory & wi-fi card & still NO power up when I put them back in after letting it sit for a while. I guess the only thing is to open up the laptop & pull the cmos batt to reset that.
 
Any thoughts on this new problem after Linux attempt?

---

### Post by utilitytrack on 2010-10-20
> **dh390 said:**
> Is it possible for Ubuntu to corrupt or damage the computers bios?

No, it's not possible. But you think right that it's some hardware problem. What exactly version of Ubuntu you tried? If it's 10.10, then I can advice you don't rush use it, because it's very beta. Try stable 9.10 and tell us your impressions.

---

### Post by heyjean on 2010-10-20
> **utilitytrack said:**
> No, it's not possible. But you think right that it's some hardware problem. What exactly version of Ubuntu you tried? If it's 10.10, then I can advice you don't rush use it, because it's very beta. Try stable 9.10 and tell us your impressions.
just as utilitytrack said, it may be the problem of the version you downloaded, so take it easy and try use the more stable version and wish luck for you.

---

### Post by coffeecat on 2010-10-20
@dh390, I agree that you should try to reset your CMOS. Ubuntu wouldn't damage the BIOS.

I also agree that if you have issues with 10.10 you might want to try an earlier version, but I must comment on this:

> **utilitytrack said:**
> If it's 10.10, then I can advice you don't rush use it, because it's very beta. Try stable 9.10 and tell us your impressions.

10.10 is **not** beta. I have it running on three machines - one desktop and two laptops - and it's as stable as a rock for me. And I've seen plenty of positive recommendations around the forum. There will be problems with some combinations of hardware; this is inevitable and happens with every release, but to say it is unstable on that basis is illogical and misinformed.

Also, support for 9.10 will last only another 6 months. The most recent LTS release, 10.04 will be supported for more than 2 years and the 10.04.1 ISO is now available which irons out a few glitches that were present when 10.04 was first released.

---

### Post by Quackers on 2010-10-20
On your first attempt to install did you use a capital letter in your user name? This is normally the reason for the forward button to be greyed out.

---

### Post by asifsolkar on 2010-10-20
> **Quackers said:**
> On your first attempt to install did you use a capital letter in your user name? This is normally the reason for the forward button to be greyed out.


I used Capital Letter in the username there was no problem with that , I could easily login even in Pc name i used First Alphabet as capital no problem with that.

---

### Post by utilitytrack on 2010-10-20
> **coffeecat said:**
> 10.10 is **not** beta. ...And I've seen plenty of positive recommendations around the forum. 

No problem, I can find much more (three hundred thousand) and best recommendations on the same forum: [http://www.google.com/search?hl=en&newwindow=1&safe=off&q=problem+site%3Aubuntuforums.org+%2Bmaverick&btnG=Search]("http://www.google.com/search?hl=en&newwindow=1&safe=off&q=problem+site%3Aubuntuforums.org+%2Bmaverick&btnG=Search")

> **coffeecat said:**
> There will be problems with some combinations of hardware... 

Yes, the reasons of all problems it's hardware.

> **coffeecat said:**
> ...but to say it is unstable on that basis is illogical and misinformed.


No sense in quarrel about terms. All who are interested welcome to [https://bugs.launchpad.net/ubuntu]("https://bugs.launchpad.net/ubuntu/+bugs?field.searchtext=&orderby=-importance&search=Search&field.status%3Alist=NEW&field.status%3Alist=INCOMPLETE_WITH_RESPONSE&field.status%3Alist=INCOMPLETE_WITHOUT_RESPONSE&field.status%3Alist=CONFIRMED&field.status%3Alist=TRIAGED&field.status%3Alist=INPROGRESS&field.status%3Alist=FIXCOMMITTED&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package="). Make your own conclusions.

---

### Post by TBABill on 2010-10-20
Did you change the name of the computer to be different than your real name? I have not tried it but I know when I enter my real name as "Bill" it automatically names the computer "bill-laptop" (with whatever word I want in place of laptop). I never change the first part from bill- because it generates during my typing of my name as Bill. Did you make this different than what you put in as your name? Just a guess but I think they need to match whatever you put into the name block, but in lower case only, before the "-" where you can change it to whatever after the dash.
 
I sure hope that made sense!!! I'm confused now and I wrote it! ;)

---

### Post by Quackers on 2010-10-20
> **asifsolkar said:**
> I used Capital Letter in the username there was no problem with that , I could easily login even in Pc name i used First Alphabet as capital no problem with that.


The "problem" was that "it only had the "Back" icon accessible to click on."
With all lower case letters the "forward" button would be accessible.

---

### Post by TBABill on 2010-10-20
Right. I was, in a really obscure way, asking if the Real Name and user name were different OTHER than capitalization. When you type in your real name the system automatically populates it in the username block, only in lowercase. I was just curious if the OP had tried to change the username to be totally different than the real name, which I am not sure you can do.

---

