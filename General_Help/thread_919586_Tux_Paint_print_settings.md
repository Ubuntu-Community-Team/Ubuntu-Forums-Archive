---
title: "Tux Paint print settings"
date: 2008-09-14
forum: General Help
---

### Post by Arphahat on 2008-09-14
Even when I hold ALT the print dialog doesn't come up in Tux Print.  What I'd like to do is configure it to print on the whole page, instead of the tiny area it does.  Any help is appreciated.

---

### Post by Arphahat on 2008-09-16
Hey, maybe this isn't the right place to ask for help about a specific app.  Can anyone suggest a good place to look for help on Tux Paint?

---

### Post by Aearenda on 2008-09-16
Have you seen [http://www.tuxpaint.org?](http://www.tuxpaint.org?)

Also, do you have the tuxpaint-config tool installed?

---

### Post by Arphahat on 2008-09-16
I have looked at that site, but didn't see any forums.  I did install the config-tool and set it to always display the print dialog, but it never does.  When we print, it always uses a tiny area of the paper, and my daughter would prefer that it use the whole thing.  Any idea on how to do that?

---

### Post by Aearenda on 2008-09-16
I just did a test print on my system and it did produce a sensible size. 

What happens if you print to the PDF printer (as a diagnostic test, I'm not suggesting this as a fix)? You'll need to set it as the default printer temporarily since tuxpaint won't ask you. 

Also, is your printer set to a very high dots-per-inch value? Are there any scaling options in the printer settings?

---

### Post by Aearenda on 2008-09-16
Looks like you're not alone - here's a workaround: [http://ubuntuforums.org/showthread.php?t=626926](http://ubuntuforums.org/showthread.php?t=626926)

I can't get it to show the printer options either. Clues here: [http://www.tuxpaint.org/docs/html/README.html](http://www.tuxpaint.org/docs/html/README.html)

---

### Post by Arphahat on 2008-09-17
Thanks a bunch!  I'll have to give that a shot when I get home.

---

### Post by Arphahat on 2008-09-17
Err... I don't mean to be dense, but I live most of my life in the world of Windows, so after looking at the script for printing full size, I have no idea what I need to do.  Do I need to copy and save that as a file somewhere?  I tried typing in the "cat $HOME/bin/tuxprint" but it replies with "cat: /home/andy/bin/tuxprint: No such file or directory".  Sorry, and thanks!

---

### Post by Aearenda on 2008-09-18
No worries, I went through the same transition. Here's what to do, with some minor variations from the original:

1. Go to the Applications Menu, and choose Accessories->Text Editor. This will start the program 'Gedit'.

2. Paste the following text into the screen:```

#!/bin/bash
# Script to reformat tuxpaint output
# Based on http://ubuntuforums.org/showpost.php?p=4041784&postcount=5

FILE=$(ls -rt $HOME/.tuxpaint/saved/*.png | tail -1)
pngtopnm $FILE | pnmtops | lpr

```

3. Do File->Save As and simply name the file .tuxprint
(The dot at the beginning of the name makes it a hidden file).

4. Next we need to make the .tuxprint file executable. To do this, go to Places->Home, so that the file browser (Nautilus) opens up showing your home directory.

5. On the 'view' menu, click on 'show hidden files'.

6. Find the file you just made, called .tuxprint, and right-click on it.

7. Choose 'Properties' from the context menu, and then open the 'Permissions' tab.

8. Check the box marked 'Allow executing file as program'

9. Click 'Close'

10. Now we need to tell Tuxpaint to use this script. First, in Nautilus check to see if .tuxpaintrc exists; if it does, open it (it should open in Gedit), otherwise go back to Gedit and do File->New.

11. Now paste the following at the end of the file:```

printcommand=/home/<yourusername>/.tuxprint
```
Be sure to replace <yourusername> with your user name!

12. If the file already existed, do File->Save; otherwise, do File->Save As and name the file .tuxprintrc

13. Now close Gedit.

14. Next we need to install the netpbm package, so go to System->Synaptic Package Manager. If this is the first time you have run it, you will need to dismiss the intro page.

15. Look for 'netpbm' in the 'Package' column, and double-click it. 

16. Click on 'Mark' to accept the dependency package libnetpbm10.

17. Click on the 'Apply' button on the tool bar, and then on 'Apply' on the confirmation dialogue.

18. Wait for it to finish.

19. Click on 'Close' to finish the process, and then close Synaptic.

20. That should be it! Close Tuxpaint if it is running, then open it and try to print a picture. 
****Note that it will always print ***the most recently saved*** picture, so if you open an existing one, you will need to re-save it first! ****
It will still go to the default printer, and with the default settings, but the image should be bigger. If it works, fine; otherwise, we will have to use the command line to diagnose why not :-)


Caveat: I have tried this, but I can't tell if it really works since it would make no difference on my system - I suspect the problem is triggered by printer type.

---

### Post by Arphahat on 2008-09-18
Hey, thanks a bunch!  

I followed your steps and tried saving and then printing; unfortunately, I do not see a difference in what gets printed.

---

### Post by Aearenda on 2008-09-18
Ok, then I think you should explore your default printer settings. Go to System->Administration->Printing; select your printer in the left pane, and look at the printer options tab on the right. If there is a 'printer resolution' option, try changing it to a lower dots-per-inch figure - mine is 600dpi.

You may also be able to do something like this in the .tuxprint file - where it says ```
pngtopnm $FILE | pnmtops | lpr
```try putting```
pngtopnm $FILE | pnmtops -imagewidth 8 | lpr
```

---

### Post by Arphahat on 2008-09-19
OK, I have looked at my printer settings, but there doesn't seem to be any type of dpi settings, unfortunately.

I also tried changing the line as you suggested with no effect.  Hmm...

---

### Post by Aearenda on 2008-09-19
Weirder and weirder...

If you use Nautilus to go to .tuxpaint/saved, and right-click on one of the images there, then open it with Firefox, and then print it, what size is it?

---

### Post by Arphahat on 2008-09-19
One of them is:
Width: 608 pixels
Height: 472 pixels

One I created with the new script installed:
Width: 832 pixels
Height: 664 pixels

---

### Post by Aearenda on 2008-09-20
Sorry, I mean how big is the print from Firefox on the paper?

---

### Post by Arphahat on 2008-09-20
Oops!  No, I'm sorry, I guess I fail "reading".

The image prints full size via Firefox, the way I would want it to look in Tux Paint.  So, the probably means that whatever is wrong is probably on Tux Paint's side, right?

---

### Post by Aearenda on 2008-09-20
I think it's a combination of tuxpaint and your particular printer, since on my system tuxpaint gets it right. Can you start a terminal (from Applications->Accesssories) and post the output from the following commands please (maximise the terminal, and use the mouse to select, right-click to copy and then paste the output into the reply box): 
```
cat /etc/papersize
grep papersize /etc/tuxpaint/tuxpaint.conf
grep print /etc/tuxpaint/tuxpaint.conf
grep DESC /etc/lsb-release
apt-cache showpkg tuxpaint

```

Also, what is the make and model of your printer? Is it local or shared on another system?

---

