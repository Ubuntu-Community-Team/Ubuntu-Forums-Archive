---
title: "Why is my printer listed four times?"
date: 2023-09-20
forum: Hardware
---

### Post by Paddy Landau on 2023-09-20
I have one printer (HP Envy 5030). When I installed Ubuntu 22.04 last year, I added the printer the usual way, through the settings.

But the printer is listed four times in Settings > Printers. In Additional Settings, however, it's listed twice. And, in the HP Device Manager (hp-toolbox), it's shown just the once. (See the screenshots.)

When trying to print from an app (e.g. from LibreOffice, Chrome, wherever), I see two printers to choose from. They both work, albeit with slightly different options available.

This isn't a problem, but in the interests of curiosity, I would love to know what's going on — why is the printer listed four times in the settings, twice in the additional settings and apps, and once in the HP Device Manager?

---

### Post by #&amp;thj^% on 2023-09-20
This has been seen a lot over the past years, Paddy will you try this to see if any disappear:
```
systemctl stop cups-browsed

```

---

### Post by Paddy Landau on 2023-09-21
> **1fallen said:**
> This has been seen a lot over the past years, Paddy will you try this to see if any disappear:
```
systemctl stop cups-browsed

```
Thanks for the suggestion. I ran it, and it made no difference. So, I restarted the computer, and…

It made it worse &#129315;

It's still listed four times in the settings, twice in apps and once in HP Device Manager, but now, instead of twice, it's listed four times in the Additional Settings.

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=292756&stc=1[/IMG]

It's quite a mystery!

As I say, this isn't a problem for me. I'm merely curious as to what's happening.

Thinking about it, this printer supports WiFi Direct and AirPrint. Could that be a part explanation? The printer also supports scanning (as so many do these days). Would one of the entries be the scanner?

---

### Post by #&amp;thj^% on 2023-09-21
That sounds like a  reasonable explanation. Mine is not quite that new still churning away on my 4800 series.

---

