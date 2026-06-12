---
title: "Gnome Phone Manager"
date: 2008-07-04
forum: Hardware
---

### Post by steveneddy on 2008-07-04
I just discovered this useful application by searching for a way to send SMS messages from my laptop.

I already had a mobile phone that could send messages, and this little app will integrate with your cell phone via Bluetooth so you can send messages from PC to phone (so the phone can send the message) and when you get an SMS message on your phone, it will pop up on your PC.

I thought this was a great addition to my already busy desktop, but I have found it to be a handy tool when you don't have to remember where you put the phone just to send an IM to someone. As long as the phone is within Bluetooth range and you have the application started, you can send and receive SMS messages and do it all from your desktop.

It's in the repos.

```
sudo apt-get install gnome-phone-manager
```

Here's the web site to tell you more.

[http://live.gnome.org/PhoneManager](http://live.gnome.org/PhoneManager)

:D

---

### Post by pavel989 on 2008-07-05
sounds interesting. good find

---

### Post by steveneddy on 2008-07-05
> **pavel989 said:**
> sounds interesting. good find

Thanks. I've already sent a few IMs and it works very well.

Feels like a regular IM client, kind of like Pidgin.

I use a Motorola Moto Razr.

---

### Post by rudihawk on 2008-07-05
Does it work with Sony Erricson phones?

---

### Post by hongleong on 2008-07-05
I can't get gnome-phone-manager to work with my Sony Ericsson K610i, connected via the serial USB cable.

> **$ gnome-phone-manager**
** Message: bdaddr
** Message: New connection device is /dev/ttyACM0 (changed)
** Message: New connection device is /dev/ttyACM0 (not changed)
** Message: Connecting...
** Message: Status 1
** Message: Making serial port connection
Couldn't open PHONET device: Operation not permitted

** (gnome-phone-manager:13629): WARNING **: gn_gsm_initialise: Command failed
** Message: Failed connection to device on /dev/ttyACM0
** Message: Exiting connect thread
*[COLOR="DarkSlateGray"]^C[/COLOR]*

$ **sudo gnome-phone-manager**
** Message: bdaddr
** Message: New connection device is /dev/ttyACM0 (changed)
** Message: New connection device is /dev/ttyACM0 (not changed)
** Message: Connecting...
** Message: Status 1
** Message: Making serial port connection
Couldn't open PHONET device: Inappropriate ioctl for device

** (gnome-phone-manager:13639): WARNING **: gn_gsm_initialise: Command failed
** Message: Failed connection to device on /dev/ttyACM0
** Message: Exiting connect thread
*[COLOR="DarkSlateGray"]^C[/COLOR]*

These are the versions that I've installed:
- gnome-phone-manager: 0.40-3
- gnokii: 0.6.22.dfsg-3

This is my ~/.gnokiirc:

> [global]
port = /dev/ttyACM0
model = AT
initlength = default
connection = serial
use_locking = yes
serial_baudrate = 19200
smsc_timeout = 10
[xgnokii]
allow_breakage = 0
[gnokiid]
bindir = /usr/sbin/
[connect_script]
TELEPHONE = 12345678
[disconnect_script]
[logging]
debug = off
rlpdebug = off
xdebug = off

gnokii can identify my phone connection successfully:

```
$ gnokii --identify
GNOKII Version 0.6.22
IMEI         : <snipped>
Manufacturer : Sony Ericsson
Model        : AAD-3022041-BV
Product name : AAD-3022041-BV
Revision     : R1KG001 070418 2238
```

I can successfully send SMS via gnokii command line:

> echo "hello world" | gnokii --sendsms +<number> -r

Somehow gnome-phone-manager just doesn't work. Any help will be appreciated. Thanks. :)

---

### Post by steveneddy on 2008-07-05
I will admit that I'm no expert at this application, but i can point you to the bug list.

If it's not in the bug list, you could add a bug to get this working better for you and others with the same issue/phone.

[Bug List]("http://bugzilla.gnome.org/buglist.cgi?query_format=advanced&short_desc_type=allwordssubstr&short_desc=&product=gnome-phone-manager&long_desc_type=substring&long_desc=&status_whiteboard_type=allwordssubstr&status_whiteboard=&keywords_type=allwords&keywords=&bug_status=UNCONFIRMED&bug_status=NEW&bug_status=ASSIGNED&bug_status=REOPENED&bug_status=NEEDINFO&emailassigned_to1=1&emailtype1=substring&email1=&emailassigned_to2=1&emailreporter2=1&emailqa_contact2=1&emailcc2=1&emailtype2=substring&email2=&bugidtype=include&bug_id=&chfieldfrom=&chfieldto=Now&chfieldvalue=&cmdtype=doit&order=Reuse+same+sort+as+last+time&field0-0-0=noop&type0-0-0=noop&value0-0-0=")

---

### Post by hongleong on 2008-07-07
steveneddy, thanks for introducing the gnome bugzilla. I've logged the [bug]("https://bugs.launchpad.net/ubuntu/+source/gnome-phone-manager/+bug/246173") at Launchpad Ubuntu instead, since the hardy repo has the older version of gnome-phone-manager. :)

---

### Post by steveneddy on 2008-07-08
You are welcome.

I hope you get your issues resolved.

---

### Post by motang on 2008-07-14
Cool, I shall try this out with my Samsung u520 when I get home.  Thanks for the heads up.

---

### Post by 00chilli00 on 2009-04-04
Hey all, i love this program lols
It works with out a problem on my sony ericsson.
Thanks

---

### Post by steveneddy on 2009-04-06
Maybe when I get time I'll plug my Blackberry into this to see if it works.

---

### Post by AlexanderDGreat on 2010-01-14
It doesn't work on some phones, how do you receive message, mine doesn't show up.

---

### Post by steveneddy on 2010-01-14
man this is an old thread - did you try the web site?

I don't even use this anymore....

---

### Post by AlexanderDGreat on 2010-01-16
Yeah, but it seems there are so few apps for mobile phones out there, wammu, gammu, etc... But it's ok, I got mine working already, I just needed to restart. Thanks.

---

### Post by xile_ on 2010-04-10
the gnome-phone-manager application only allows for 160 character messages, does anyone have an idea on how to bypass this restriction?

I know what the Wammu application supports concatenated messages - but I like the simplicity in the gnome-phone-manager app :)

---

