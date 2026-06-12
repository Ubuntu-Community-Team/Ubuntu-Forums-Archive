---
title: "a few problems with kmail..."
date: 2005-11-23
forum: General Help
---

### Post by shrink on 2005-11-23
just wondering if anyone out there has experienced these problems, or has any good ideas. it's all new to me so any help would be most appreciated.

initially things were all going fine, but at some point a few weird things have happened and i don't know why.
i) the font for my messages has changed, but only in the main panel, not on the header of the message. if i adjust the font manually in the settings, it still changes the header section but the main text stays in dejavu sans mono. everywhere else the fonts are fine. i've looked everywhere i can think of to change the font to no avail.
ii)when i select a hyperlink in a message, rather than opening this directly in konqueror(which it used to do), it now saves the hyperlink code into a directory called /var/temp/kdecache-struan/ and then opens that in konqueror. all this shows me is a bunch of what i assume is the hyperlink code. i've got no ideas how to fix this at all.

thanks for any suggestions

---

### Post by mlomker on 2005-11-23
[QUOTE=shrink]i) the font for my messages has changed, but only in the main panel, not on the header of the message. if i adjust the font manually in the settings, it still changes the header section but the main text stays in dejavu sans mono. everywhere else the fonts are fine. i've looked everywhere i can think of to change the font to no avail.[/quote]

I'm not following.  Are you talking about the line with the subject/date/time but the preview is correct?  Perhaps posting a screenshot would be helpful.

> ii)when i select a hyperlink in a message, rather than opening this directly in konqueror(which it used to do), it now saves the hyperlink code into a directory called /var/temp/kdecache-struan/ and then opens that in konqueror. all this shows me is a bunch of what i assume is the hyperlink code. i've got no ideas how to fix this at all.

Go into Tools, Configure Konqueror, File Associations, and then look under text for the HTML extension.  What do you have listed for Application Preference Order?  

I use Firefox, so that's the first thing listed for me.

---

### Post by shrink on 2005-11-23
[QUOTE=mlomker]I'm not following.  Are you talking about the line with the subject/date/time but the preview is correct?  Perhaps posting a screenshot would be helpful.

a screen shot would be a good idea, but alas i don't know how to do that.  i'll try explaining it again...in kmail the fonts are ok everywhere except in the body of the messages, this is in the preview plane or if i open the message properly.  the weird bit is that the header (with subject etc) is in the correct font, and this can still be changed using the settings but the text in the message itself cannot.  i don't even know what font it currently is, maybe deyjavo sans mono?

Go into Tools, Configure Konqueror, File Associations, and then look under text for the HTML extension.  What do you have listed for Application Preference Order?  

I use Firefox, so that's the first thing listed for me.[/QUOTE]

konqueror is the only thing in that list, it's also the only one if i look at the file associations through the settings/kde components/file associations
could i have accidently deleted an important package? as i did install firefox to start but then decided just to go with konqueror and so removed it.

---

### Post by shrink on 2005-11-24
well i've been mucking around and have managed to solve the hyperlink problem. i had to change 'konqbrowser' to 'konqueror' under the browser section of the kde component chooser in the settings folder. i seem to remember that this was what it was before i had changed it to firefox.  i guess when i uninstalled firefox it may have reset this wrongly because i didn't have to enter that manually.

on the font problem, i discovered that i can still change the font as it's running off the 'fixed width font' and now that i look at the window the text is only going part way across the page despite the large window. anyone know how i can fix this?

thanks

---

### Post by mlomker on 2005-11-24
[QUOTE=shrink]on the font problem, i discovered that i can still change the font as it's running off the 'fixed width font' and now that i look at the window the text is only going part way across the page despite the large window. anyone know how i can fix this?[/QUOTE]

You should use ksnapshot to capture/post a screenshot of what you are talking about.

---

### Post by shrink on 2005-11-24
thanks, but it's sorted now as after discovering that the font was changable in the settings using the fixedwidth font i then hunted for a setting to turn this off and voila.  i don't know when or how i changed this but good to get it right. 
the only other thing is that i can't get kgpg to prompt me for my passphrase for emails in my inbox but i understand that that is a known bug that will get fixed in the future.

thanks for your help

---

