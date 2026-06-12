---
title: "Ekiga - basic help"
date: 2008-07-26
forum: General Help
---

### Post by phil81uk on 2008-07-26
Hello,

I have set up Ekiga using my sipgate.co.uk. I did a test call to sip:613@fwd.pulver.com which is some free testing tool. It rings and seems to work (but no audio ... will get to that).

But how do I call a regular no-sip number? I'm used to x-lite (Windows softphone), and in that I had a button to open the line, which gave a dial tone, and then I just punched in the number. In Ekiga I can't find how to get a dial tone!

Also, when I called the echo test, I speak and I can see the meter showing my mic level going up, but not so for the audio. Maybe it's the testing service. I guess I can do a live test once someone has told me how to get a dial tone!

BTW, when I log into sipgate it shows my phone as offline, so I dont know. I have added sipgate.co.uk into accounts.

---

### Post by ramjet_1953 on 2008-07-26
Ekiga doesn't seem to like [COLOR="Blue"]Pulse Audio[/COLOR].

Navigate to [COLOR="Blue"]System>Preferences>Multimedia Systems Selector
[/COLOR]
When the window opens, select [COLOR="Blue"]ALSA[/COLOR] for both output and input plugins.

[COLOR="Red"]NOTE[/COLOR]: If Multimedia Systems Selector is not listed in your System>Preferences Menu, just open [COLOR="Blue"]System>Preferences>Main Menu[/COLOR] and when the window opens, make sure there is a tick in it's listing in the [COLOR="Blue"]Preferences Menu[/COLOR].

I could be wrong, but I don't think Ekiga supports calling regular telephones. Even if it did, you would need to subscribe to a company that provides this service, and pay for it.

The Linux version of Skype does provide this and you can buy Skype-Out credits.

Regards,
Roger :cool:

---

