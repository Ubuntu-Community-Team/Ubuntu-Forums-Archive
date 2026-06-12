---
title: "HP Laserjet 1320 driver problems"
date: 2006-06-28
forum: Hardware &amp; Laptops
---

### Post by doc_solitude on 2006-06-28
Hello,

I hope this is the right place to post! My problem is slightly related to [ this ]("http://ubuntuforums.org/showthread.php?t=158083&highlight=laserjet+1320+dapper") thread. Except for that printing works unsatisfying no matter which application I use.

Let me explain further: 
I have a HP Laserjet 1320 printer, which worked well under various distributions (gentoo, debian and ubuntu breezy) with either the linuxprinting.org's PPD file or the postscript driver shipped with breezy. 
Some days ago I updated my breezy installation to dapper which made the printer stop working. I had to change the driver. Accidentally I changed it to the hpijs driver listed as "Laserjet 1320 hpijs" in the KDE printer setup. This did not work satisfying. On a printout of a pdf file containing some images and diagrams certain diagrams were only black boxes. I noticed my mistake and wanted to change to the right driver, i.e. the postscript driver. And there my problem starts:
Selecting the driver listed as "Laserjet 1320 series" works and the data gets send to the printer. But before printing the error light blinks and the printer does nothing. When I press the Go button (green button) the file gets printed and all images are displayed right, but the the printout is not propperly aligned to the paper. I checked wheter I set the right paper format (A4). It's the same story with the PPD file from linuxprinting.org.
When I try to select the driver listed as "HP Laserjet 1320 (Foomatic + Postscript)" (it is offered to you when you select Laserjet 1320 and press next) I get to see this message:

[I]Unable to load the requested driver:
Unable to create the Foomatic driver [HP-LaserJet_1320,Postscript]. Either that driver does not exist, or you don't have the required permissions to perform that operation.[/I]

I am in administrator mode, which (up to my understanding) gives me the necessary rights. The foomatic-db-gimp-print foomatic-db-gutenprint foomatic-db-hpijs packages are installed.

Is there any possibility to get the printer to work with the postscript driver, as it did in breezy, or am I stuck to the hpijs driver for the moment?

Thanks in advance!

doc

**Edit:** I found out that the problem has already been described in this bugreport: [#42965]("https://launchpad.net/distros/ubuntu/+source/kdeprint/+bug/42965")
In the discussion of this bug two possible solutions were mentioned: 
The first one was to run "sudo foomatic-cleanupdrivers". This solved the problem with the dialog saying something about missing rights.
The second solution was to copy the driver manualy to "/usr/share/ppd/custom/". Unfortunately this didn't solve anything.

---

### Post by pete83 on 2006-07-08
I just want to let you know that you are not alone in this issue. I installed dapper fresh on a clean hard drive, and the my LaserJet 1320 has the same symptoms that you describe: the PostScript driver has messed up margins, and it has an error first so that I have to push the "go" button before it even prints.

And the poor-quality hpijs driver works with perfect margins and no errors.

I'd really like to get this issue solved, because the PostScript is much better quality, and the printer's great PostScript support in Linux is the whole reason I bought the printer.

Has anybody solved this yet?

---

### Post by pete83 on 2006-07-08
Actually, what I said above was the summary of how it behaved a few weeks ago.

I just tried it again, after typing in "sudo foomatic-cleanupdrivers," and the printer works differently. I don't know if it is the result of an update, or if it is the result of the above command.

Anyway, the new way the PostScript driver behaves is this: the paper size and margins are now perfect, but I still have to push the "go" button on the printer before it will print. So it could still use some work, but I guess it works good enough now...

---

### Post by doc_solitude on 2006-07-10
I tried what you proposed. After an upgrade (which installed a new cupssys) I  ran "sudo foomatic-cleanupdrivers". The printer now behaves as you described. Its behavior is still unsatisfying, but it gets better!
Thanks for your reply!

Greetings,

doc

---

### Post by tenjin on 2006-07-10
Hi,

I've just bought a LaserJet 1320 and am trying to get it working under Ubuntu, and through SAMBA, Windows XP.

I too get the "won't print until I press the green button" problem.

I also can't get duplex to work unless I set it as default for the printer rather than setting it on a per job basis.

I've got a feeling that the printer is defaulting to "Letter" format rather than A4. That would explain the margin issues and error status.

Is there anyway to check what paper format the printer is working off by default? Ubuntu seems to think it is letter.

Cheers

D.

---

### Post by pete83 on 2006-07-12
tenjin, I still get the "won't print until I press the green button" problem, but my margins and paper size are now perfect. Originally it was A4 for me, but I wanted letter. If you still have the margin trouble, check what the file "/etc/papersize" says. Also, try the "sudo foomatic-cleanupdrivers" command, which in my case may possibly have fixed it.

Also, I don't mean to insult your intelligence if you think this is obvious, but if you click on System>Administration>Printing, and then right click on the printer and go to "properties", you can change the default paper size for the printer. I don't think this is the same as the file "/etc/papersize", though, so I'd change them both.

---

### Post by sophrosune on 2006-07-13
I had the "won't print until I press the green button" problem too but I swapped over to the "hpjis - HPLIP 0.9.7" drivers and it appears to have gone away (and the printer settings displayed in the properties panel make a lot more sense too - the Paper tab with the 'recommended' drivers showed three(!) paper trays). One thing though, you may need to restart CUPS to effect the change:

sudo /etc/init.d/cupsys restart

HTH

---

### Post by doc_solitude on 2007-05-23
Hello,

it's been a long time since I started this thread. In the meanwhile I didn't use ubuntu or linux. Instead I used a mac. Now, I'm back to ubuntu and it was just today, that I tried to configure my printer again.
I still had the same problem with ubuntu, but I also had it on the mac. 
The solution that worked for me (on both systems) is quite simple!
You have to use tray 2 (maybe it works also with tray 3) as the primary media source.
To do this point your browser to [http://localhost:631](http://localhost:631). Then click on "Printers" and on this page on "Set Printer Options".  The page that you see now is split into several sections. Search the one called "General". The option you want is called "Media Source". Select "Tray 2" there. You might have to enable tray 2 on top of the page.
The steps I describe above were done under xubuntu 7.04.

Maybe somebody stumbling over this post is happy to find this information.

cu doc

---

### Post by pete83 on 2007-07-31
Thanks for the tip... but I must say, over the intervening months, I have grown fond of the "push the go button to print" bug, and so I am hesitant to try your solution now. I think I might actually miss giving a big confirmation-button-push to my print jobs.

---

### Post by pete83 on 2007-08-02
Actually, I just tried this and it worked.

Thanks, doc!

---

### Post by mpvano on 2007-08-07
The proposed solution using the Cups web interface won't work if you don't own the printer or if it's a networked printer.

Here's the only way I've found to control your local options for printing on a networked printer in cups:

From the command line try:

lpoptions -o HPOption_Tray2=True

(at least this works on Debian Etch and on the Macintosh - note that you might need to use the sudo prefix to the command on some platforms....).

You can find many other interesting options (as well as how to add ones that aren't present on your cups configuration) by using the commands:

lpoptions -l

and

man lpoptions


I hope this helps someone else....

Mario

---

### Post by pete83 on 2007-08-08
> The proposed solution using the Cups web interface won't work if you don't own the printer or if it's a networked printer.

Hey thanks for the tip, but this is not true. The proposed solution does work for a networked printer. I am printing to a networked printer (using a Linksys WPS54G print server) over the ipp protocol, and I can change the settings that my computer uses with the CUPS url:  [http://localhost:631](http://localhost:631) 

I don't know if there is something wrong with your computer maybe (or are you perhaps not using Ubuntu? maybe your distribution doesn't even have CUPS installed...), but you should still have to set up the driver on your own computer, regardless of where the printer is, and that's what CUPS is for...

---

### Post by mpvano on 2007-08-09
Perhaps I expressed that too strongly.

I should have said it "may not work" rather than it "won't work". It certainly doesn't work here for the LTS version of Ubuntu.

All the networked printers here on machines using Ubuntu 6.06 LTS (3 of them) show grey buttons in the gnome print manager dialog with no options available in the panes for HP printers shared via our Macintosh computers running CUPS.

Other configurations may or may not work as you say. Have you tested EVERY configuration?

The lpoptions command does, in fact work on these Ubuntu machines, however.

I can't speak for Feisty (Feisty doesn't work at all for us due to known show-stopping bugs that have not been fixed and apparently will not be fixed with our Thinkpads, Dell 2400s and 2350s and so we had to switch to Etch to keep working)

Perhaps your networked printers have options that can be set from the GUI, but it certainly doesn't work that way on any of ours. CUPS has many operating modes depending on the level at which the printers are shared.

Your print server based solution almost certainly doesn't act the same as our configurations because your linksys is a RAW print server and the printer is shared at a lower level - it spools raw printer output. That means your printer rasterizing takes place in the client machines, not the print server and so many options need to be controlled in a different way.

Cups (at least some of the many versions) apparently does NOT set up raw print spooling by default when printing to some peer machines - it depends on the version of CUPS on the other end and the options used in building it - and that's why the options don't appear for us (and many other users).

I didn't come here to argue, only to explain why some things need to be done with the lpoptions command - it's too bad most people don't know it exists.

Furthermore, if you take the time to actually run the command, you will see that for many printers it is the ONLY place to set EVERY printer option - the various GUIs leave out the ability to control options that the authors thought were not important, but which can and do make printing unusable.

Be careful of assuming that because a solution works for you that it's true for everyone.

Mario

---

### Post by pete83 on 2007-08-09
> Perhaps I expressed that too strongly.

I should have said it "may not work" rather than it "won't work". It certainly doesn't work here for the LTS version of Ubuntu.

Ah, then maybe I worded my reply too strongly as well. Perhaps I should have said it "could work" rather than it "does work." Mario, you're right that I am using Feisty, and I will be switching to Gutsy soon. I am sorry to hear about bugs that prevent you (and others) from upgrading.

I am happy with the way I have it working, but I can't deny that lpoptions looks like a great tool. It's true that I had never heard of it before. We are both trying to help people, but it seems clear that our local networks are different.

Anyways, peace.

Peter

---

