---
title: "No Display"
date: 2011-11-26
forum: Hardware
---

### Post by dRounse on 2011-11-26
I don't really know where else to go to ask this question. I have a Gateway E series desktop (the slim one like schools use) I got it from a school, and when I turned it on I saw that you needed a password and username, because the school didnt reset the computers. It worked fine other than not logging on to WinXp  but i booted Linux and looked around a little, I took it out the other day to turn it into a home server, it had been away for 6 months, and now there is no display on the monitor. I know the VGA cable is good because I use it for my desktop that I'm using to type this. It worked the first day i took it out and then when i went to install Ubuntu Server there was no display. I took it apart and and cleaned it out and made sure nothing was loose. I plugged everything back in and it worked. Now, its been about a week with it off, and I turned it on and no display again.(I never installed Ubuntu Server) I really on't feel like taking it apart again, because there must be another reason for there to be no display. Any help would be greatly appreciated.

---

### Post by dandnsmith on 2011-11-27
Sounds like some hardware has failed.
Do you get any beeps when you turn on?
Are there any sounds/disk activity suggesting that the system is going through a bootup?
When you did have it working, did you ever get into the BIOS to look at settings?

---

### Post by dRounse on 2011-11-27
> **dandnsmith said:**
> Sounds like some hardware has failed.
Do you get any beeps when you turn on?
Are there any sounds/disk activity suggesting that the system is going through a bootup?
When you did have it working, did you ever get into the BIOS to look at settings?

Yes I did look at the BIOS and everything looked fine and yes when i turn the computer on i have it booting from the CD drive and that turns on, so i know its booting, but it's weird that it wont display, and its kind of a bummer because I really wanted to use this, I have another computer I can use so I should be ok.

---

### Post by dandnsmith on 2011-11-28
If it really is booting from the CD, then either you've disturbed something while cleaning, or the graphics has failed.
Fairly easy to put a graphics card in, but I'm not sure about the BIOS display if you have onboard graphics (as you may need to disable it).

---

### Post by dRounse on 2011-11-28
> **dandnsmith said:**
> If it really is booting from the CD, then either you've disturbed something while cleaning, or the graphics has failed.
Fairly easy to put a graphics card in, but I'm not sure about the BIOS display if you have onboard graphics (as you may need to disable it).


Last night I got it to work again, as I put DBAN in to wipe it so I could install the server it beeped three times and froze, I shut it off and then rebooted it, it came up to the menu that says press F10 for boot menu and it froze on that page. I didn't have any luck after that, the computer is kind of junk anyway, so it's not a huge deal.

---

### Post by dandnsmith on 2011-11-29
The beeps can tell you what is the probably cause - if you know the BIOS.
I don't know the gateway PCs.

---

### Post by dRounse on 2011-11-29
> **dandnsmith said:**
> The beeps can tell you what is the probably cause - if you know the BIOS.
I don't know the gateway PCs.

That's ok thanks for the help... I am going to build my own server from newegg, then I am going to install Ubuntu Server 11.10, I want to make it so I can access it from anywhere, so someone said it needed to be sftp, I'm not sure how to do this, because this is the first time I'll be setting up a server.

---

