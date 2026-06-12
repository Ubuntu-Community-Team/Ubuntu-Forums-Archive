---
title: "Funny printing problem with Canon PIXMA MP140"
date: 2013-05-04
forum: Hardware
---

### Post by turboscrew on 2013-05-04
I have Canon Pixma MP140 shared via Samba/Cups.

I was paying bills with another machine running Windows Vista.

After paying I printed out the receipts.

First one  - OK.
Second one - OK.
Third one - the printing failed: The job was seen in Cups web page as "being processed", but nothing came out.
  I cancelled all jobs and printed it again from the Windows machine. Tried to turn off the printer - but it didn't.
  Just the power light was left blinking. So I did a "power chord reset" and printed again from the windows machine and
  it printed OK.
4th one OK.
5th  one - the printing never ended: The job was seen in Cups web page as  "sending data", and the printer indicated processing, but
  nothing came out. I cancelled the printing, did the "power chord reset" to the printer and reprinted from Cups.
  It printed OK.

At  some point (I don't remember where) I saw some notification that Cups  was waiting some indication from the printer, but I guess it never came?

Tried  now with another printing. The job was seen in Cups web page as  "completed", but the printer still indicates processing something.
After about 5 mins I made the "power chord reset".

The funny thing is, I used to have an older MoBo with Puppy installed and there was no problems with the printer then,
and the printing was MUCH faster eve if otherwise the system was slower. In puppy I had Samba-TNG + Cups + PIXMA MP150 drivers.

The questions are:
  a) How could I find out what's wrong (which logs etc.)
  b) Do 150-drivers work better than 140-drivers?
  c) Is Samba much slower than Samba-TNG? (with old setup printing took  about 15 seconds, with current setup about 1 minute and 10 seconds)

Current Samba is 2:3.6.6-3ubuntu5
Current Cups is 1.6.1-0ubuntu11
Current  driver is Driver:    Canon PIXMA MP140 - CUPS+Gutenprint v5.2.9 (color,  2-sided printing) (I don't know how to find out the MP140 driver  version).

Then I bumped into this.

[http://ubuntuforums.org/showthread.php?t=2070247&highlight=pixma+mp140](http://ubuntuforums.org/showthread.php?t=2070247&highlight=pixma+mp140)

Which package should I downgrade? printer-driver-gutenprint?
And to which version?
And should I use PM140 or MP150 drivers?

Has anybody tried Raring's packages with PIXMA MP 240? I understand it uses Cups 1.6.2-1ubuntu5.

The [https://launchpad.net/~till-kamppeter/+archive/ppa]("https://launchpad.net/%7Etill-kamppeter/+archive/ppa")
 only has one Quantal package: cups-filters, and no cups-related Raring packages.

Also, ppa:michael-gruz/canon has no packages for Quantal or Raring. just Oneiric and earlier.'

---

