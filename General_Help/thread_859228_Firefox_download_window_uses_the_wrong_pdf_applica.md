---
title: "Firefox download window uses the wrong pdf application"
date: 2008-07-14
forum: General Help
---

### Post by laser_in_your_eye on 2008-07-14
I have my default pdf program set up for acroread in ubuntu, and any pdf file I click on opens correctly.  However, when I download a file in firefox and try to open it by clicking on the file in the Download Window, it opens with Evince.  Does anyone know how to change the pdf default in the Download Window?

Thanks!

---

### Post by mikewhatever on 2008-07-14
There should be an option saying 'other'. Click there and point firefox to whatever you use.

---

### Post by Valsodar on 2008-07-14
Yes, got to edit->preferences->applications. Those are the firefox default applications to use. change them as your heart desires.

Edit:
Ooopss. my bad, it appears that that title was misleading, applications do not feature all the doc types just some. So pdf is not in it. :(

---

### Post by tramir on 2008-07-14
I think double-clicking in the Downloads window opens the file with the default application in Gnome. Which happens to be Evince. What you can do (but keep in mind that this will affect opening PDF files from Nautilus from now on) is to go to Places-Home folder, navigate to a folder that contains a pdf file, right click on it, choose Properties, go to the "Open with" tab and select Adobe Reader. This should make Acrobat the default pdf application.

---

### Post by coffeecat on 2008-07-14
> **Valsodar said:**
> Yes, got to edit->preferences->applications. Those are the firefox default applications to use. change them as your heart desires.

Edit:
Ooopss. my bad, it appears that that title was misleading, applications do not feature all the doc types just some. So pdf is not in it. :(


Which is interesting, because if I go to edit > preferences > applications in Firefox (3) here, 'PDF Document' **is** listed. And under 'Action' it's showing 'Always Ask'. Which is nice of it.

Curious.

---

### Post by laser_in_your_eye on 2008-07-14
> **tramir said:**
> I think double-clicking in the Downloads window opens the file with the default application in Gnome. Which happens to be Evince. What you can do (but keep in mind that this will affect opening PDF files from Nautilus from now on) is to go to Places-Home folder, navigate to a folder that contains a pdf file, right click on it, choose Properties, go to the "Open with" tab and select Adobe Reader. This should make Acrobat the default pdf application.

Good suggestion, but I have already done this and any pdf I try to open outside of the Firefox download window responds correctly.  I've also tried changing the settings in edit -> preferences -> applications, and that doesn't do anything for me.  I also just realized that this problem is not limited to pdf files--anything I try to open by clicking on the file in the downloads window opens with the original gnome defaults (even though I have changed them in Nautilus).

Any other suggestions?

---

### Post by mikewhatever on 2008-07-14
As I said in the second post, simply change it in the window that's asking you what to do. Instead of choosing the default option of 'Open with Gedit' point choose other and then point it to the executable of the program you want. Tick the 'do it every time box too.

---

### Post by laser_in_your_eye on 2008-07-14
> **mikewhatever said:**
> As I said in the second post, simply change it in the window that's asking you what to do. Instead of choosing the default option of 'Open with Gedit' point choose other and then point it to the executable of the program you want. Tick the 'do it every time box too.

There is no window asking me what to do.  The option you mentioned in the second post does not appear in the Downloads window (at least not in FF 3).  Right-clicking on a file in that window only gives the following options:  Open, Open containing folder, Copy download link, Select all, and Remove from list.  I think we might be talking about different issues.  My only problem is in the Downloads window (see Tools -> Downloads).  Thanks anyway.

---

### Post by mikewhatever on 2008-07-14
> **laser_in_your_eye said:**
> There is no window asking me what to do.  The option you mentioned in the second post does not appear in the Downloads window (at least not in FF 3).  Right-clicking on a file in that window only gives the following options:  Open, Open containing folder, Copy download link, Select all, and Remove from list.  I think we might be talking about different issues.  My only problem is in the Downloads window (see Tools -> Downloads).  Thanks anyway.

Welcome. If you just read and don't make things up, everything would be fine. The window I've been talking about is the one that opens when you click on a link to a file while browsing. I won't repeat everything already said, it's getting boring and apparently has no effect. Good Luck.

---

### Post by edge_nabby on 2008-08-19
i have the same problem. does anybody know how to change file associations for firefox download manager?

---

### Post by 1/0 on 2008-08-22
I had similar problems with ktorrent and solved this by removing all sections containing torrent in the file: .mozilla/firefox/12345678.default/mimeTypes.rdf (adjust the profilename). In your case remove all lines/sections containing pdf. Start at *<RDF:Description...* until either */>* or *</RDF:Description>*. Make a backup of the file just to be sure if you do anything wrong.

---

### Post by BlueSkyNIS on 2009-03-25
Well, in Fedora it's even worse! When I click XLS (spreadsheet) file instead to open OpenOffice it opens wine-preloader?!

---

### Post by mathaifenn on 2011-05-11
> **mikewhatever said:**
> Welcome. If you just read and don't make things up, everything would be fine. The window I've been talking about is the one that opens when you click on a link to a file while browsing. I won't repeat everything already said, it's getting boring and apparently has no effect. Good Luck.


[LIST=1]
[*] Click on the download button in firefox......opens window  of downloaded files. Set pdf to be opened by program B and click it to NOT ASK.
[*]Now close and open firefox, go the download window and right click on the files. You no longer have the chance to correct it as mentioned above.
[/LIST]

---

### Post by mathaifenn on 2011-05-11
> **mikewhatever said:**
> Welcome. If you just read and don't make things up, everything would be fine. The window I've been talking about is the one that opens when you click on a link to a file while browsing. I won't repeat everything already said, it's getting boring and apparently has no effect. Good Luck.
I find the tone of the message rather harsh. If you set your preferred application in the firefox download window and click don't ask me again... it does not give you the option for "other" as you had said. So NOW who is jumping to conclusions?

---

