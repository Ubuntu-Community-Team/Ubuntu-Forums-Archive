---
title: "SMS app for Ubuntu"
date: 2008-07-15
forum: General Help
---

### Post by S3loth on 2008-07-15
I have tried Kopete, but SMS wouldn't show up after I installed SMSsend. I found this list: [http://tuxmobil.org/phones_linux_sms.html](http://tuxmobil.org/phones_linux_sms.html)

but that's very daunting, considering most of them probably aren't that great. Anybody know of any that are good?

---

### Post by brian_p on 2008-07-15
> **S3loth said:**
> I have tried Kopete, but SMS wouldn't show up after I installed SMSsend. I found this list: [http://tuxmobil.org/phones_linux_sms.html](http://tuxmobil.org/phones_linux_sms.html)

but that's very daunting, considering most of them probably aren't that great. Anybody know of any that are good?

I am familiar with smssend and it works well for me. The problem is  not with the program itself but with the scripts used with it. Many are out of date because a website changes and this is what you might have experienced. The same could probably be said for some on the program list on tuxmobil.

What sms site are you trying to use? In the end you might have to write your own script.

---

### Post by S3loth on 2008-07-15
My phone uses verizon, but I can't find a vtext one. Do you know of any good scripts. btw I don't know how to program beyond CSS lol

---

### Post by brian_p on 2008-07-15
> **S3loth said:**
> My phone uses verizon, but I can't find a vtext one. Do you know of any good scripts. btw I don't know how to program beyond CSS lol

You're stuck with searching for one then. 'vtext script sms' and variations might get you a script.

---

### Post by steveneddy on 2008-07-15
[This]("http://ubuntuforums.org/showthread.php?t=849874") **might** help.

---

### Post by MarkReaves on 2009-09-03
Well it isn't the best solution but to send SMS messages on Linux, go to the Yahoo Web Messenger and log in. You can add mobile contacts and message them and they can message you.

[http://webmessenger.yahoo.com/](http://webmessenger.yahoo.com/)

Someone really needs to work on getting an sms messenger for Linux though since cell phones and text messaging are becoming so popular. I have to use a computer based app to send SMS messages from my home since I don't get cell reception here.

---

### Post by mamdez on 2010-12-11
I just found an easy app with a GUI that requires no command line tweeking.  It should work on all linux x86 distros.  Just extract the program file from the archive and click on it.  Here's the link [http://www.sw4me.com/wiki/CellMessenger](http://www.sw4me.com/wiki/CellMessenger)
 The only change that may be needed is for those using USB modem sticks (the app website only mentions cell phones but it works with USB modems too and their Help guide explains this).  In the Setup you will select connection type: serial port.  Then type in the serial port instead of using the options in the drop-down box.  For example I typed, /dev/ttyUSB1 to connect to my USB modem (Huawei E1552), and I am using a prepaid service on a GSM/HSDPA network.  Then select fast or full sync and hit "apply".  That's it.  I typed a message and synced and was able to both send and retrieve all the messages that I have not been able to read on my USB stick over the past few months.  If you are a novice and don't know which port your USB is on, the easiest thing to do is to type dmesg at the command line prompt while your USB modem is plugged in.  While watching your screen plug then unplug your modem to see which "tty" disappears and reappears then use that as your port.
 
On a side note, I was able to send sms text messages using UMTSMON but could not receive anything.  Also I would get an error message saying the message was "not sent OK" after sending; however, the messages where actually sent.  I confirmed this by sending a message to my cell phone and from the messages I was just able to retrieve using the Cell Messenger program.  UMTSMON sends the messages after registering on the network without being actually connected to network. I have tried a ton of other programs.  None of the native apps worked for me (gnome phone manager, gammu, kphone etc.) and I tried Vodafone (Betavine project), Mobile Partner, etc.  I am so happy I found Cell Messenger, that I had to share.

---

### Post by look1 on 2011-07-08
Here is a simple and run directly script, I have been using for a couple of months
Especially for several or just a couple of message per month.
Their website provide registration for free SMS to try. no expire. The website [http://www.sms4mail.com/smsmail/smscmd.php](http://www.sms4mail.com/smsmail/smscmd.php) . 

Usage is Simple


[LIST]
[*][FONT=Arial]**Syntax              : ./smscmd.sh 'phone1,phone2,phone3' 'Simplest to send sms in       linux ' 'email' 'password'**[/FONT]
[*][FONT=Arial]email and password is what you      have registered the website [/FONT][FONT=Arial][URL="http://www.sms4mail.com/smsmail/register.htm"]   
[/URL][/FONT]
[/LIST]

---

### Post by imblack on 2011-07-29
You could also install kannel and configure it then you can send and receive SMS in ubuntu. Also look for gammu.

The main problem is that your phone doesn't behave as a good, compatible GSM modem. I had that problem, did some research and bought SonyEricsson w200i which is so far the best one I found for the task at hand.

I have used kannel for my own hobby project  [SMS to Pakistan]("http://loop.pk") :)

---

