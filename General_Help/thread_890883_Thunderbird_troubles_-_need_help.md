---
title: "Thunderbird troubles - need help"
date: 2008-08-15
forum: General Help
---

### Post by PT.Linn.A on 2008-08-15
OK, so here is where I own up to being a Noob.

I made the full switch to Ubuntu 8.04 and would like to use Thunderbird as my mailer.

I installed Thunderbird, and Lightning. And, that all went well. However, when I used Synaptic to delete Evolution I began having trouble receiving email in Thunderbird. Any thoughts??

Also, how can I setup Thunderbird to use Arial fonts?

---

### Post by Roasted on 2008-08-15
Wait, what issues exactly are you having with Thunderbird? What email service are you using? (gmail, yahoo, etc)

---

### Post by cariboo on 2008-08-15
Are you using your ISP's fully qualified domain name in the server section? that may be a part of your problem, if you don't know your ISP's fqdn, give them a call they will be happy to give it to you.

As to your font problen it looks like there is only a choice of Sans and Sans Serif.

Jim

---

### Post by PT.Linn.A on 2008-08-15
I am using Gmail for email. My ISP is Comcast.

The trouble is this:

When first installed all emails came to my Thunderbird inbox right away. However, after deleting (Marked for full removal) Evolution I received NO emails in my Thunderbird inbox.

I re-installed some of Evolution and I now receive email ... but at a CONSIDERABLY slower rate. (They will sit on server for some time (12+ hours) before making it to Thunderbird inbox.

I also have a comcast.net email address - that I rarely use - and it is experiencing the same issues.

---

### Post by PT.Linn.A on 2008-08-15
If I'm using Gmail is the ISP all that important?

Thunderbird setup the Gmail account beautifully. The trouble began after I deleted Evolution.

---

### Post by silkstone on 2008-08-15
Deleting Evolution is not a good idea. Unfortunately it is intertwined with other things including the Gnome desktop. There are parts you can remove, but not all of it.

I suggest reinstalling Evolution completely. Then uninstall and reinstall Thunderbird. Your mail folders should be preserved, but you can back them up from ~/.mozilla.thunderbird/XXXX.default/Mail

---

### Post by PT.Linn.A on 2008-08-15
Thanks **silkstone**.

I had fear that the answer you gave was going to be the one I received. But, at least now I know.

Can I remove Evolution from the drop menu: Applications>Internet>Evolution Mail

If so, how?

---

### Post by silkstone on 2008-08-15
You will probably find that it won't let you do that, because Evolution is linked to Gnome packages that should not be removed. Best to reinstall the original Evolution packages from Synaptic.

Removing and reinstalling Thunderbird shouldn't be a problem - the configuration files are in your Home folder and should remain.

---

### Post by PT.Linn.A on 2008-08-15
I appreciate the quick responses and help.

Thanks to all.

:D

---

### Post by silkstone on 2008-08-15
In case it helps you to put things back as they were, here are the Evolution packages that are installed in Hardy by default...

evolution
evolution-common
evolution-data-server
evolution-data-server-common
evolution-exchange
evolution-plugins
evolution-webcal

---

### Post by Too Late on 2008-08-15
> **PT.Linn.A said:**
> Can I remove Evolution from the drop menu: Applications>Internet>Evolution Mail

If so, how?
Yes, you can. Go to System -> Preferences -> Main Menu. Find Evolution and uncheck it. (I think it's also in Office folder by default, so uncheck that also, if you like.)

---

### Post by PT.Linn.A on 2008-08-15
WOW! The help here is AMAZING!

Thanks **Too Late**

---

### Post by PT.Linn.A on 2008-08-15
OK ... so I re-installed Evolution. But, now it is messing with Firefox.

If I have Thunderbird running I have only Hotkeys in Firefox. (When I hit a key it opens up a menu and does not type a character.)

Any ideas as to what happened? Or, better yet, how to resolve the issue?

Phoenix

---

