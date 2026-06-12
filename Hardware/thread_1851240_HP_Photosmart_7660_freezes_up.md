---
title: "HP Photosmart 7660 freezes up"
date: 2011-09-27
forum: Hardware
---

### Post by lonewolfandcub on 2011-09-27
I'm having issues with my HP Printer( Photosmart 7660). For some reason it seems to freeze up when I ask it to print a document. I have the HP patch installed, and it worked the first few times, then started freezing up again. I can't even turn it off without unplugging it. Usually, I'll go through Windows and print a bogus document, then go back and restart Ubuntu (10.10) and upon startup it spits out the document. In addition to that it refuses to print out my Sudoku Puzzles. I can't have my morning coffee without my sudokus! I tell it to print out my puzzles, it goes to the page showing my printer, I click "Print" and nothing happens. It used to do the same thing under Lucid Lynx, I was hoping the problem would be taken care of with Maverick Meerkat and the HP program add-on which downloaded with the installation process. Guess not. Anyone have any suggestions, I would love to completely abandon Microsoft, they're rich enough as it is.

---

### Post by agillator on 2011-09-28
I have seen references to it before but don't know what the 'HP Patch' is. Enllighten me, perhaps? On the other hand, I have a number of HP printers, some quite ancient, and have no problem. A couple of them are Photosmart series printers. I removed Ubuntu's HPLIP package and loaded HP's HPLIP package and everything seems to work fine. HPLIP is not what you are referring to as the patch, are you?

---

### Post by lonewolfandcub on 2011-09-28
HPLIP is exactly what I have, but I didn't have to after it, the installation program directed me to it, I think... it's been a while, I may have gone surfing on the net trying to correct the problem and come across it. On the other hand, I tried the latest version of Ubuntu 11.(?), and it too had issues with my printer. Only after running the debugging program, which I don't believe I've seen on my current versions of Ubuntu(10.4 Maverick), did it manage to print out my puzzles, and that without the HPLIP program. I called it a patch but it may not be a patch, I'm not exactly a super computer dude, only a Sunday night fiddler. So some terms may be used incorrectly, sorry about that.

---

### Post by agillator on 2011-09-29
I would try this, then:
    Download HPLIP from HP ([http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html)).
    Remove Ubuntu's version of HPLIP (sudo apt-get purge hplip).
    Run the installer you downloaded and then do the setup for your printer.

Once it is set up, see how your printer functions. If there are problems, on the HP site you accessed above, go to the knowledge page and look up your printer and see what it says there. That should tell you if something simply isn't supported, but I don't think you will find a problem from what I saw. If that is true, then go to their support page from the menu and ask HP for help. My impression is that, although they are not loud about it, they do support their printers on Linux. As I said before, I have a number of HP printers and they seem to be fully functional with no problems. 

I hope this helps a bit, at least.

---

### Post by lonewolfandcub on 2011-09-29
Thanks for the tip, I'll give it a try this weekend, for now I don't have the time to look into this, but the advice is sound. This is why I love the Ubuntu Community, there is always someone within who is in the know. Have you ever out of curiosity tried to contact someone within the Microsoft world? It just isn't done, everything cost something there, it's $50 right off!

---

