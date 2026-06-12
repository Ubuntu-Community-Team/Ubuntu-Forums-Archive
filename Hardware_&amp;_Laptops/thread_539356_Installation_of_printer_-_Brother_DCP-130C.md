---
title: "Installation of printer - Brother DCP-130C"
date: 2007-08-31
forum: Hardware &amp; Laptops
---

### Post by doctorbrowder on 2007-08-31
I'm hoping somebody can guide me through this printer/scanner/copier installation...

I bought a Brother DCP-130C specifically because I read that it had Linux Debian drivers. I'm having trouble installing it, though. I went to the Brother website and downloaded the driver they have listed for this make & model, and it is now in the Home folder. When I go through the System --> Administration --> Printing menu, and go through the "Add A Printer" wizard, I can only get as far as Step 2 of the wizard. In Step 2 of the Add A Printer wizard, it does not have my model listed, so I clicked on the "Install Driver" button. It then opens another window and says "Select a PPD file", but my driver that I installed from the Brother website does not appear (possibly because of its name, "dcp130ccupswrapper-1.0.0-10.i386.deb"?) but when I click on the PPD Files radio button and select "all' files" there it is. When I select the file driver name and press the Open button, a curt box opens up telling me "Only files ending with .ppd or .ppd.gz will be installed." and it sends me back to the beginning of step 2.

So, what am I doing wrong?

Thanks!

---

### Post by doctorbrowder on 2007-08-31
OK, I've gone to the Brother FAQ page for Linux systems at <http://solutions.brother.com/linux/sol/printer/linux/linux_faq-2.html#120>.

It says 

[I]I'm using Debian/Ubuntu Linux. My Brother model name is not listed in the CUPS Web interface.

1.Ensure that csh/tcsh is installed.
2. Copy the PPD file from "/usr/share/cups/model/xxxxx.ppd" to "/usr/share/cups".
(where "xxxxx" stands for your model name)
2. Restart CUPS.
3.The model name should now be listed in the model list.[/I]

OK, that's great, BUT NOW what is csh/tcsh???????

---

### Post by Colbrac on 2007-09-03
csh and tcsh are programs that give you a command prompt (a shell) with slight differences to other shells like 'bash' and the gnome terminal. But that doesn't matter much. The main point is that the Brother software needs it installed. See [http://ubuntuforums.org/showthread.php?t=105703](http://ubuntuforums.org/showthread.php?t=105703) for a description of installing the driver for a similar Brother printer.

---

