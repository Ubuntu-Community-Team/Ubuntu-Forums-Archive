---
title: "help to repair or uninstall evolution mail"
date: 2008-08-21
forum: General Help
---

### Post by pandar57 on 2008-08-21
Hi

I'm new to Ubuntu.  I'm running Ubuntu 8.0.4.1 as a virtual appliance in VMWare Fusion on the Mac.  I'm having difficulty with Evolution Mail.  I've come to believe that I need to uninstall/reinstall Evolution, or run a repair on it.  When I try to do that in Add Remove application, I get nowhere.  Can someone help?

Pandar57

---

### Post by pytheas22 on 2008-08-21
What exactly is giving you trouble with Evolution?  It may help to reinstall it with:
```

sudo apt-get remove --purge evolution
sudo apt-get install evolution
```

If the problem only affects your local user account, then moving the .evolution folder would probably fix it:
```

mv ~/.evolution ~/.evolution-OLD
```

***Note that if you have any mail saved locally in Evolution, the above steps may cause you to lose it, so back it up first (if your mail is stored on the server, it won't be touched)***

If the above doesn't help, please describe your problem in more detail so that we can look into other solutions.

---

### Post by pandar57 on 2008-08-21
> **pytheas22 said:**
> What exactly is giving you trouble with Evolution?  It may help to reinstall it with:
```

sudo apt-get remove --purge evolution
sudo apt-get install evolution
```

If the problem only affects your local user account, then moving the .evolution folder would probably fix it:
```

mv ~/.evolution ~/.evolution-OLD
```

***Note that if you have any mail saved locally in Evolution, the above steps may cause you to lose it, so back it up first (if your mail is stored on the server, it won't be touched)***

If the above doesn't help, please describe your problem in more detail so that we can look into other solutions.

Thanks for response

I'm having trouble getting Evolution to Send any mail.  The problem that lead me to believe that I needed to uninstall was due to my own user ignorance.  Maybe an uninstall isn't needed.  I've configured a Gmail account and a Cox.net account.  Both work to receive emails, but I can't send in either account.  I've configured both accounts in Mac and Windows environments, but can't seem to conquer Evolution.  I configured Thunderbird mail on Ubuntu, and it works fine to send and receive mail, so I don't know what's up.  Help will be greatly appreciated.

Pandar

---

### Post by pytheas22 on 2008-08-21
If sending mail is the issue and it never worked on Evolution, then I don't think that reinstalling Evolution is the solution.  You probably just need to figure out the correct smpt settings to put into Evolution.  I've had similar problems in the past where receiving mail works fine but I can't send anything.

Double-check the settings under the "Sending Email" tab in Evolution.  If you just guessed on some of the settings, try playing around with them to see if you can hit the right ones.  If your email provider publishes documentation on configuring your account for Thunderbird or Outlook, and if you provide a link to it, I'll take a look and see what I think should be in Evolution.

Also, there are several guides on the Internet for configuring Gmail on Evolution.  [This]("http://tuxicity.wordpress.com/2007/03/08/howto-set-up-gmail-in-evolution-gnomes-mail-client-and-organizer/") and [this]("http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/41552-complete-guide-using-gmail-thunderbird-mozilla-mail-evolution-kmai.html") may be useful.

---

