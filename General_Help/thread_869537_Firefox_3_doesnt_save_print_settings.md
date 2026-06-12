---
title: "Firefox 3 doesnt save print settings"
date: 2008-07-24
forum: General Help
---

### Post by Dr_Snapid on 2008-07-24
I upgraded to Hardy and therefore Firefox 3 and I have found that it isn't saving print settings.

For example, I need to enable 'print background colours' and 'print background images' and also I turn off the text that appears in each corner (page numbers, url etc). At the moment I have to set these options every time I print, for some reason they arent saved. They saved fine in firefox 2. 

I also noticed the print dialogue has changed a fair bit. I dont like that the 'print selection only' option has moved and is now in the options tab rather than the first tab, but thats just an annoyance. I can live with that, but i really want the other stuff to save. 

Can anyone offer any ideas?

---

### Post by Dr_Snapid on 2008-08-03
This is so bad I have stopped using Firefox and am using epiphany.

Can someone at least tell me if they have this same problem? Try printing any web page, under options change the settings. Then when you print again, see if the setting remain?

Thanks in advance

---

### Post by lidex on 2008-08-09
Dr,
Go into about:config in Firefox. Type "print" in the filter box. Scroll down to this setting:"print.save_print_settings". Double click that line to change value to "true".
Report back.

---

### Post by dr.wong on 2008-08-17
Okay I see there was never a report back.

I have upgraded to FireFox 3 on Ubuntu and the printer settings arent saved.

I use ubuntu with a web-based point of sale system so I need to set all of the stuff around the printout to --Blank--. This worked fine in FF2.

I've tried the config change mentioned above, the value was already true before I clicked on it. I changed it to false and back a few times but it just doesn't seem to register.

Any suggestions anyone??

This is quite an urgent annoyance.

---

### Post by dr.wong on 2009-07-04
Does anyone know if this has been resolved in 3.5?

---

### Post by b_i_b on 2009-08-10
I have to agree this is a major pain in the (_|_) :(.

I am stuck uysing FF2 because of this, this is not a upgrade this is a hindrance.

At least if the settings could be saved, with FF2 if you had a framed window (I use SQL-ledger) it would print the active frame, now with FF3 it's print > options > print selected frame EACH time I want to print a report or invoice.

not good

---

### Post by dr.wong on 2009-08-13
MAJOR FAIL.

I can't believe this STILL hasn't been fixed! I started a thread a while ago offering to write a FF Plugin if someone could show me a good tutorial on how to do it but I got no responses..

Does NO ONE have a workaround?

---

### Post by wprime on 2009-09-05
Set your ideal settings, then print something with the default printer, the settings will save then.

---

### Post by dr.wong on 2009-09-05
> **wprime said:**
> Set your ideal settings, then print something with the default printer, the settings will save then.


I will try later, but the method you have mentioned is the exact problem with FireFox 3. It doesn't save the settings even after printing.

---

### Post by wprime on 2009-09-06
> **dr.wong said:**
> I will try later, but the method you have mentioned is the exact problem with FireFox 3. It doesn't save the settings even after printing.

Well I use Firefox 3 and found this thread because I was having the exact problems, because I too use it as a point of sales system and the header and footer weren't particularly eye catchy on the invoices and I kept having to set them each time.

But I remembered I got it working before I reinstalled it yesterday so I fiddled around a bit and found after printing something from the default printer and the settings have saved as that ever since.

---

### Post by freedisk on 2009-11-16
I have a fix for this one! Took me a few minutes, but I figured it out. Works for Firefox 3.5.

1. Type about:config in the address bar.
2. Type 'header' or 'footer' (depends which one you want to edit) in the Filter box. You should now see a couple of lines like:

*print.printer_(your printer).print_headerright*
or
*print.printer_(your printer).print_footerright*

They have values listed at the end of the line (like *&U, &PT, &D*). You can edit the different lines by rightclicking on them.

You can set the default values for each printer now. I know &U stands for URL. I bet you can figure out the rest.

---

### Post by mfseeker on 2009-11-28
[SIZE=2]Firefox 3.5 in Karmic still doesn't save settings for me. I have tried every about:config setting that seemed relevant. I don't know what relevance the header or footer settings might have. I am trying to save the resolution. It always defaults to 300x300 DRAFT. Most annoying, as more than one person has complained.
[/SIZE]

---

### Post by DocDanW on 2010-01-08
I am having this exact-same problem with Ubuntu 9.10 and Firefox 3.5.3 through 3.5.7.

After scouring the forums and the 'Net, I have tried every suggested fix, to no avail; I can change the printer settings and they hold *once* before reverting to Draft settings.

This is bad enough that I am ready to leave the Ubuntu fold and return to the Windows 7/XP options of my tri-boot setup...I can print everything normally in Ubuntu except when I try to print in Firefox.  What good is web browsing if all you can do is print in draft?

Please...is there a resolution for this terribly frustrating problem?  Things worked fine in 9.04 for me and when I ran Firefox 3 in my Wubi install of 9.10.  The problem seems to be specific to Firefox 3.5x _as included in_ 9.10.

---

### Post by roberthr on 2010-01-26
I also have this problem with different printers on different  locations. Every other application retains settings but Firefox defaults  to 300 dpi which renders graphics useless. Even latest nightly build of  Firefox does not help. 
  

It's not user friendly not to mention how much more paper is used ;-)

---

### Post by anselm on 2010-01-26
> **lidex said:**
> Dr,
Go into about:config in Firefox. Type "print" in the filter box. Scroll down to this setting:"print.save_print_settings". Double click that line to change value to "true".
Report back.

Have you tried this yet??? dr

---

### Post by DocDanW on 2010-01-28
Yes; I tried changing the print settings in about:config, but with the same results...the problem still persists.    Worse, the changes I made in about:config did not hold either.  After restarting Firefox, the settings I changed were reset to their default values.  Following advice in various FAQs and forums, I also looked for any user-preference .js files that might be over-riding the changes in about:config.  No luck there, nor did it help to delete the prefs.js file, and I failed to locate any numbered .js files that could influence the settings.  I have four machines in my care, all used by noobs to surf the 'Web.  They're all disturbed printing "doesn't work like it used to" and want me to "make it like it was before".  I can't, and feel frustrated.  Any ideas for what to try next?  With many thanks in advance. -- Dan.

---

### Post by roberthr on 2010-01-29
I have just noticed that Thunderbird has the same problem!
So what's making both Mozilla products ignoring printer settings???

---

### Post by Zer0Nin3r on 2010-09-01
> **freedisk said:**
> I have a fix for this one! Took me a few minutes, but I figured it out. Works for Firefox 3.5.

1. Type about:config in the address bar.
2. Type 'header' or 'footer' (depends which one you want to edit) in the Filter box. You should now see a couple of lines like:

*print.printer_(your printer).print_headerright*
or
*print.printer_(your printer).print_footerright*

They have values listed at the end of the line (like *&U, &PT, &D*). You can edit the different lines by rightclicking on them.

You can set the default values for each printer now. I know &U stands for URL. I bet you can figure out the rest.

This works just fine.  Thank you.

---

### Post by CrusaderAD on 2011-01-19
> **freedisk said:**
> I have a fix for this one! Took me a few minutes, but I figured it out. Works for Firefox 3.5.

1. Type about:config in the address bar.
2. Type 'header' or 'footer' (depends which one you want to edit) in the Filter box. You should now see a couple of lines like:

*print.printer_(your printer).print_headerright*
or
*print.printer_(your printer).print_footerright*

They have values listed at the end of the line (like *&U, &PT, &D*). You can edit the different lines by rightclicking on them.

You can set the default values for each printer now. I know &U stands for URL. I bet you can figure out the rest.

This worked for me. Thanks!

---

### Post by Yoey on 2011-02-08
Been struggling with this for years!

I think I may have found something new, although it's tough to tell if it actually helped or not since I've changed so many things in about:config...

Anyways, I noticed that for some of the other settings (not for header and footer, which can be changed easily in about:config), including zoom level and 'auto-shrink-to-fit' will be saved if you change them in "print preview" but not if you change them from the normal print dialog.

Just noting this hear in case it helps someone or in case I run into it again later.

---

### Post by arkinfazli on 2012-12-17
Yep, print-preview did the trick.
nice one!

Arkin

---

### Post by sisco311 on 2012-12-17
Old thread closed.


[[img]http://ompldr.org/tYnpyNw[/img]](http://ompldr.org/vYnpyNw)


From the [code of conduct](http://ubuntuforums.org/index.php?page=policy) that you agreed to when you created your account:

> 
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.


---

