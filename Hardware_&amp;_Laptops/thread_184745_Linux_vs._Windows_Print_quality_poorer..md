---
title: "Linux vs. Windows Print quality poorer."
date: 2006-05-30
forum: Hardware &amp; Laptops
---

### Post by shane2peru on 2006-05-30
Ok, let me say first that I have an HP PSC 1315 working very well under Ubuntu 5.10 - up-to-date with the 1310 drivers.  I'm impressed in that the setup was super easy.  However I'm dual-booting, and have noticed when I print a text document in Ubuntu the print (black) is about a 90% black - slightly less black than when I print the same document in Windows.  The print out in Windows looks much sharper, and darker.  I know it is a small thing, but it is a big deal, since I do a lot of desktop publishing for distribution, as well as letters, etc.  I want my things to look good.  Any ideas on how to fix this?  Anyone else noticed this problem?  Thanks.

Shane

---

### Post by patrick295767 on 2006-05-30
[QUOTE=shane2peru]Ok, let me say first that I have an HP PSC 1315 working very well under Ubuntu 5.10 - up-to-date with the 1310 drivers.  I'm impressed in that the setup was super easy.  However I'm dual-booting, and have noticed when I print a text document in Ubuntu the print (black) is about a 90% black - slightly less black than when I print the same document in Windows.  The print out in Windows looks much sharper, and darker.  I know it is a small thing, but it is a big deal, since I do a lot of desktop publishing for distribution, as well as letters, etc.  I want my things to look good.  Any ideas on how to fix this?  Anyone else noticed this problem?  Thanks.

Shane[/QUOTE]
 
Very interesting ! :-) 
What is the program you are using to print your documents under windows and Linux ?
  
Did you try to pass via PDF format ? That's giving most time very good quality.

Greetz

---

### Post by shane2peru on 2006-05-30
Patrick,

I always use OpenOffice under both OS.  I like having my work available under both platforms.  I can print the exact same document under both, and have different results.  I want to stress that the text is clear, there is not a single problem with being able to read the text, or anything to do with a font issue.  It is like using a brand new marker on Windows, and using a marker that you kids have used for a while - the color, and brilliance, and boldness is just not there.  I know my ink cartridges are fine, because I printed in Linux first, then the same doc in windows about 20 minutes later, and there was a difference.  Thanks though. - I have used the PDF feature in the past, however it is not a font issue.  

Shane

---

### Post by Lord Illidan on 2006-05-30
System -> Printers

Select your printer, rightclick, Properties.

Go to Advanced.

Change the field Resolution, Quality, Ink Type, Media... to anything with Black + colour cartridge.

Leave Printout mode as before

---

### Post by shane2peru on 2006-05-30
I must say the test page is quite impressive, it used to be different.  I set it to:  High Quality (Color cartridge)  - there wasn't an option with both.  Under the Resolution, Quality, Ink Type, I can select up to 600dpi with color and black.  The black is just not as black as the windows printout of the same thing.  Even on the test page 100% on the black is just not as bright as the Windows black printing is.  It is almost as though it is not using the printer to its fullest potential.  The difference is like using a pencil and a black ball point pen - they are both black, but there is a difference in the niceness of it.  I don't know. Thanks for the help though, I learned a little more - I didn't know all those settings were in there. - If anyone else can suggest something - great - I really don't want to settle for second best, and this is a hold back on linux.  

Shane

---

### Post by g-a-c on 2006-05-31
Sounds to me like the driver isn't telling the printer to use the black cartridge correctly, and it's trying to create black by mixing CMY together (similar to what the single cartridge colour printers used to do years ago, before printers that held two carts became common). I don't know why this would be the case, nor can I think of a sensible way to test it, but that's what it sounds like.

---

### Post by Lord Illidan on 2006-05-31
Well... take it this way... you are wasting less black ink.

---

### Post by nocturn on 2006-05-31
I've seen this on the HP printer of a friend too (also Linux).  It uses the other colort to make black, but not the black cartridge.

Not good financially

---

