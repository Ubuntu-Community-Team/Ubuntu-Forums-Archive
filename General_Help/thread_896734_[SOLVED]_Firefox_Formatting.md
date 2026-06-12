---
title: "[SOLVED] Firefox Formatting"
date: 2008-08-21
forum: General Help
---

### Post by CrusaderAD on 2008-08-21
I noticed when I print a page out of firefox in Ubuntu, the formatting is WAY different than that of Internet Explorer on a Windows machine. Is there anyway to match it?

---

### Post by gobbles414 on 2008-08-21
You need to provide more information before anyone can help you. How is the formatting different in Ubuntu/Firefox than in IE/Windows? Are the fonts a different style and/or size? Is one browser printing in landscape while the other browser is printing in portrait?

---

### Post by Vivaldi Gloria on 2008-08-21
> **raptormanad said:**
> I noticed when I print a page out of firefox in Ubuntu, the formatting is WAY different than that of Internet Explorer on a Windows machine. Is there anyway to match it?

If you mean the scaling is different then enter "about:config" in the adress bar. Find the setting 

> print.whileInPrintPreview 

and double click on this parameter to change it from FALSE to TRUE. Now when you print preview, you should see scaling buttons.

---

### Post by CrusaderAD on 2008-08-22
Both browsers are printing in portrait. A Few things are different. The font, the size and most of all... the Margins. Even if you can these things to match, it doesn't line up the same way (like on an invoice).

---

### Post by gobbles414 on 2008-08-22
> **raptormanad said:**
> Both browsers are printing in portrait. A Few things are different. The font, the size and most of all... the Margins. Even if you can these things to match, it doesn't line up the same way (like on an invoice). Do you have access to a scanner? If so, would you please scan an example of Firefox/Ubuntu printing, and another of IE/Windows printing? Please make sure to label which picture is from which browser/OS, and make sure that you're printing the same content. Thanks...

---

### Post by CrusaderAD on 2008-08-25
Attached are the images for the two machines. "A" resembles the correct formatting when printed off of a windows machine in IE 7.0. "B" shows the incorrect formatting when printed from the ubuntu machine in Firefox 3.0.

---

### Post by gobbles414 on 2008-08-25
It seems like Firefox/Ubuntu is printing in landscape mode (wider), while IE/Windows is printing in portrait mode (taller). The fonts seem to be exactly the same in both printouts, so I feel that switching Firefox/Ubuntu to portrait printing will solve your problem. Please do BOTH of the procedures below, and report your results.

Procedure #1: Turn your printer on, and connect it to your computer. In Ubuntu, go *System => Administration => Printing* and left-click on your printer. As each printer uses slightly different options, I can only give you generalized instructions. Start by going into each tab to look for options relating to paper size. If you live in the USA, choose "Letter" or "US Letter". Many other parts of the world use a size called "A4". Now, go through all of the tabs again. This time look for anything that talks about *Borderless printing*, and choose "No" or "Off". Go through all of the tabs again. Now look for anything that talks about *Orientation*, and choose either "Portrait" or "Reverse Portrait". Hit the *Apply* button that's in the lower-right corner of the *Printer configuration* window, then close the window. Finally, restart your computer.

Procedure #2: After your computer has restarted, open Firefox. Your printer should still be turned on. In Firefox, go *File => Page Setup*. In there, make sure that *Format for* says "Any Printer", paper size is correct for your location (see above), and *Orientation* has either "Portrait" or "Reverse Portrait" selected. Click the "Apply" button. Close the *Page Setup* window, but leave Firefox open. Still in Firefox, go *File => Print* and change any options that talk about orientation, borderless printing, or paper size; confirm that all of these settings are correct. To apply any changes that you've made, print another copy of the Google homepage.

---

### Post by CrusaderAD on 2008-08-29
The browsers were both in portrait already. I think it has something to do with the margins. You can also clearly see that the buttons are different. In Windows you can bring up page setup and literally adjust the size of the margins. I can't find a way in Ubuntu.

---

### Post by gobbles414 on 2008-08-29
> "A" resembles the correct formatting when printed off of a windows machine in IE 7.0. "B" shows the incorrect formatting when printed from the ubuntu machine in Firefox 3.0. Oops! I accidentally got these printouts mixed up, because the thumbnail for _B_ is presented before the thumbnail for _A_.

> The browsers were both in portrait already. Okay, I took another look at image _A_ and noticed that the printout somehow got cropped during scanning. That's why I thought that it was in landscape.

> I think it has something to do with the margins. Since one of the images that you've provided is cropped, it's impossible for me to observe the difference in margins. Perhaps you could provide two new images, both of them uncropped and in color?

> You can also clearly see that the buttons are different. To be perfectly honest, I cannot see any difference in the buttons. Of course, printout _B_ is a low resolution black & white scan. So maybe some important details are missing. Nevertheless, the letter _I_ and the letter _L_ look exactly the same in both printouts. This means that your most likely using the same font in IE/Windows as you are in Firefox/Ubuntu.

> In Windows you can bring up page setup and literally adjust the size of the margins. I can't find a way in Ubuntu. Despite my confusing printout _A_ for printout _B_, the directions that I wrote in my previous post tell you how to get to *System => Administration => Printing* in Ubuntu. At least on my system, the margin options are in there in the *Job Options* tab in a category called *Text Options*.

Please don't think that I'm trying to be rude, but you need to provide better information before I (or someone else) can help you. For example, you say that the fonts and buttons are different but they look identical in the scanned images that you've provided. So please post HOW they look different to you; maybe I'm missing a subtle detail that isn't so subtle to you. Thanks...

---

### Post by CrusaderAD on 2008-08-29
> **raptormanad said:**
> Both browsers are printing in portrait. A Few things are different. The font, the size and most of all... the Margins. Even if you can these things to match, it doesn't line up the same way (like on an invoice).

System > Administration > Printing is where I can edit the margins. I think we were looking too deep into this. Hopefully I can adjust this to match. Thanks for the great replies!

---

### Post by gobbles414 on 2008-08-29
> **raptormanad said:**
> System > Administration > Printing is where I can edit the margins. I think we were looking too deep into this. Hopefully I can adjust this to match. Thanks for the great replies! Thanks for the thank you. If you change your mind and decide to provide some more details about your problem, I'll try my best to help you.:KS

---

### Post by CrusaderAD on 2008-09-19
I adjusted the magrins and got things to look fairly lined up. Now the problem is a barcode. If I adjust the size to make everything line up, the 3OF9 barcode is too small to scan. Bummer.

---

### Post by CrusaderAD on 2008-12-09
They way we resolved this was to have the page we were printing (in this case an invoice) save to a pdf, in which case the formatting is much closer.

---

