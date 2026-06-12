---
title: "Printing failed in Intrepid"
date: 2008-11-14
forum: General Help
---

### Post by Mark Phelps on 2008-11-14
I've installed Intrepid alongside Hardy and am attempting to set it up to do all the same stuff.

I've run into a real annoyance, though, in that I get an error message attempting to print from the file viewer of "too many failed attempts".

I'm trying to aling my printer for printing CDs, and since the values I set in Hardy don't seem to work in Intrepid, I have to repeatedly print, changing the settings slightly each time.  In Hardy, this was no problem.

In intrepid, after a few prints, the printing halts with this error message.  I don't understand because the printing hasn't failed once!

I rebooted once and could start printing again, but it happened again.

I've reboot again and now, I can't print.  I've opened the browser with localhost:631 and it shows the printer as "idle, accepting jobs".  So, it's not a problem with the printer, per se.

I won't go into the details because others already have for me, but I'm really getting disgusted by the things that no longer work in Intrepid!!

If I can't print, I can't upgrade; so, can someone please help?

I've tried doing searching in these forums, but I get a gazillion hits on each string I enter.  So, I posted my own thread instead.

---

### Post by Mark Phelps on 2008-11-18
Wow -- three days and not a single reply!! Good thing I was able to figure out a workaround.

---

### Post by deadowl on 2008-11-18
It always ends up just like it did in Office Space with those printers.
(I'd help if I had the opportunity to troubleshoot)

---

### Post by MrEgg on 2008-11-18
Hi all,

I too had printing issues after migrating to Intrepid (no printing to PDF, nor to some printers).

I did solve the issue by setting cups to complain mode :
```
sudo aa-complain cupsd
```

HTH someone,
Egg

---

### Post by jaime256 on 2008-12-19
I've been using Intrepid and the printing just stopped working on it? I'm getting an "error printing Can't prompt for authorization," and "error printing Too many failed attempts." I just turned on my notebook and did the updates since I started getting the printing error. Now I'm still getting the same thing. What gives??? This is .png file I had on the nas but copied the file to my desktop and I still can't print.

---

### Post by jaime256 on 2009-01-02
I decided to use my laptop again after all this time and what do you know, the printing still failed. So I decided to do a little tech work. Here's what I did and it worked.

1. Uninstall the printer that's not working.

2. I rebooted just to be sure, but I don't think you may need to do this.

3. Installed a new printer driver. I found a new driver for mine, I usually just use the recommended option which is usually the first. I also have my printer going through my nas. Yours may be directly connected, but this should still work.

4. The new printer is installed and I also found that since the printer is on a network for me, the icon also changed to a network type of printer. Pretty cool.

5. I printed a screenshot of the browser just to check and everything is working fine again.
 
6. The new desktop install didn't give me this problem so you may not have a problem if you did a clean install. Yes this is basic stuff but this OS is relatively new and it's hard to tell sometimes.

I hope this helps.

---

