---
title: "[SOLVED] Kontact / Kmail email and general oddities"
date: 2008-10-27
forum: General Help
---

### Post by marriedman on 2008-10-27
I have been using Kontact for my email client for months, but just barely a week ago, my Gmail POP setup stopped working. So I tried out the IMAP setup. That doesn't work either. I duplicate my setup in Thunderbird and it works fine, so I know it is not my setup nor Gmail funkiness.

All Kmail does is sit there saying retrieving messages. When it was set up for POP, it would just say "No new messages". It never said there was a communication problem or anything. I ran it from the Konsole to see if there were any errors there, and this is what is spit out:
```

paul@enterprise:~$ kontact
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
paul@enterprise:~$ WeaverThreadLogger: thread (ID: 1) suspended.
WeaverThreadLogger: thread (ID: 2) suspended.
WeaverThreadLogger: thread (ID: 3) suspended.
WeaverThreadLogger: thread (ID: 4) suspended.
kontact: ERROR: : couldn't create slave : Unable to create io-slave:
klauncher said: Unknown protocol 'cid'.
kontact:

```                                                     

Another thing weird about Kontact/Kmail, it is not accepting my system colors.  Here is a screencap to better explain it:
[IMG]http://i10.photobucket.com/albums/a130/phin666/Screencap.jpg[/IMG]

I don't know if the color thing is significant, but it is damn weird. Any help appreciated.

---

### Post by marriedman on 2008-10-29
I am still struggling with this problem. I purged Kontact and all associated apps and then only installed Kmail. I no longer have the color problem, but I still cannot send or recieve email. I went ahead a installed Thunderbird and set it up identically to Kmail and it works flawlessly with either IMAP or POP. Gmail IMAP is slow as hell, but it works. 

The thing that totally confuses me is that Kmail worked fine for months. What could have started this?

---

### Post by Butthead on 2008-10-29
Didn't Gmail change one of their port numbers recently?

I could have sworn getting an email from them saying to change port number 25 (I think?) to 625 (or something to that effect?). :confused:

I log in to their webpage directly (not through my email program), so it doesn't affect me directly.

---

### Post by marriedman on 2008-10-30
I have not figured out what was causing the color problem, but that issue seems to be gone. But I finally did figure out the email retrieval problem. I have my desktop assigned a static IP address so I can access it easily from my laptop. If I change it from a manual connection to a automatic configuration, lo and behold Kmail works. 

Everything else works fine with my assigned IP address; Ktorrent, Konqueror, Firefox, Thunderbird, Kopete, Akregator, Konversation, Adept... bascally anything that needs an internet connection. So why on earth would Kmail have a problem with static IP addresses?

---

### Post by marriedman on 2008-10-31
Knetworkmanager is the culprit. If you remove it though, nothing works. It is also a known bug. This is an inexcusable bug IMO.

---

