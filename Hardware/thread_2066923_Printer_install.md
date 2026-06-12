---
title: "Printer install"
date: 2012-10-05
forum: Hardware
---

### Post by mambo801 on 2012-10-05
hello

i'm trying to install a Brother DCP-J125, OS is Ubuntu 12.04 32bit, connection via USB.

so i have downloaded the driver, ran it via the ubuntu software center, and ubuntu software center says it will run in terminal.

and thats as far as i got. i know where the terminal program is but i have no idea what to do next.

if some one could please guide me with the terminal language it would be much appreciated. if you could make it a copy and paste response that would be great.

also, could someone direct me to a page that will teach me about the terminal and the language for my future benefits. aka teach a bloke to fish and he'll feed himself for life.

cheers

---

### Post by pdc on 2012-10-05
hi mambo801;

Brother offer an installer

[http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://www.brother.com/pub/bsc/linux/dlf/linux-brprinter-installer-1.0.0-1.gz&lang=English_lpr](http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://www.brother.com/pub/bsc/linux/dlf/linux-brprinter-installer-1.0.0-1.gz&lang=English_lpr)

that should do **_[COLOR="Red"]all the work for you[/COLOR]_**......

..what about give it a whirl.......see if it works.......

_______________________________________________________________________

If you want to do it yourself...........!!!!!!!!!!!

.....this is a good starting page.....

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html)

the aim will be to install

1) a [COLOR="SeaGreen"]cuspwrapper driver[/COLOR] .......*and then*.......

2) [COLOR="SeaGreen"]the lpr driver[/COLOR] .........

from here

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#DCP-J125](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#DCP-J125)

you need the .deb packages, as ubuntu uses .deb packages........

........if you want to follow this route, I can help with the specific commands.........

......... learning command lines does take a little while.......

I have subscribed to this thread, so I get an email when you reply; you can do the same if it helps.....

---

### Post by mambo801 on 2012-11-05
> **pdc said:**
> hi mambo801;

Brother offer an installer

[http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://www.brother.com/pub/bsc/linux/dlf/linux-brprinter-installer-1.0.0-1.gz&lang=English_lpr](http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://www.brother.com/pub/bsc/linux/dlf/linux-brprinter-installer-1.0.0-1.gz&lang=English_lpr)

that should do **_[COLOR=Red]all the work for you[/COLOR]_**......

..what about give it a whirl.......see if it works.......

_______________________________________________________________________

If you want to do it yourself...........!!!!!!!!!!!

.....this is a good starting page.....

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html)

the aim will be to install

1) a [COLOR=SeaGreen]cuspwrapper driver[/COLOR] .......*and then*.......

2) [COLOR=SeaGreen]the lpr driver[/COLOR] .........

from here

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#DCP-J125](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#DCP-J125)

you need the .deb packages, as ubuntu uses .deb packages........

........if you want to follow this route, I can help with the specific commands.........

......... learning command lines does take a little while.......

I have subscribed to this thread, so I get an email when you reply; you can do the same if it helps.....

sorry, ive been away for a couple of weeks.

i've had a look at the first link you suggested and it was all to much info...the do it your self option with your guidance is probably the best option.

cheers and thank you for offering to help!

---

### Post by pdc on 2012-11-05
there is probably a more detailed how-to here

[http://forums.linuxmint.com/viewtopic.php?f=51&p=645006#p645006](http://forums.linuxmint.com/viewtopic.php?f=51&p=645006#p645006)

....for the do it yourself way.........

_________________________________________________________________________________________________________________

........I realise now the brother script ........is a script.....

....you would need to copy and paste it into ..gedit........the text editor ..

.........save it in your Downloads directory as [COLOR="SeaGreen"]mambo801.sh
[/COLOR]
and then use the terminal to [COLOR="Red"]cd Downloads[/COLOR] and then 

> [COLOR="Red"]./mambo801.sh[/COLOR]

.... you could give it a try......should run well.......

---

### Post by mambo801 on 2012-11-07
> **pdc said:**
> there is probably a more detailed how-to here

[http://forums.linuxmint.com/viewtopic.php?f=51&p=645006#p645006](http://forums.linuxmint.com/viewtopic.php?f=51&p=645006#p645006)

....for the do it yourself way.........

_________________________________________________________________________________________________________________

Brother offer an installer script

[http://www.brother.com/cgi-bin/agree...ng=English_lpr]("http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://www.brother.com/pub/bsc/linux/dlf/linux-brprinter-installer-1.0.0-1.gz&lang=English_lpr")

that should do **_[COLOR=Red]all the work for you[/COLOR]_**......

..what about give it a whirl.......see if it works.......

sorry.....

........I realise now the brother script ........is a script.....

....you would need to copy and paste it into ..gedit........the text editor ..

.........save it in your Downloads directory as [COLOR=SeaGreen]mambo801.sh
[/COLOR]
and then use the terminal to [COLOR=Red]cd Downloads[/COLOR] and then 

> 
[COLOR=Red]./mambo801.sh[/COLOR].... you could give it a try......should run well.......



Bloody legend!

ok so here are the steps i followed after pdc posted the above quotes.

1. go to link [http://www.brother.com/cgi-bin/agree...ng=English_lpr]("http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://www.brother.com/pub/bsc/linux/dlf/linux-brprinter-installer-1.0.0-1.gz&lang=English_lpr")
.......the top of the page is a disclaimer......the bottom of the page is the script......

2. select all of the script and copy it

3. paste it into ..gedit........the text editor ..

4. save it in your Downloads directory as [COLOR=SeaGreen]mambo801.sh[COLOR=Black]

5. open the Downloads folder

6. locate the file you've just saved, and right click on the file to open the right click menu.

7. select Properties at the bottom of the menu.

8. select the Permissions tab

9. read down the list to Execute, and click/place a tick in the option box "Allow executing file as program"

10. click close.

11. now open the Terminal window/program.

12. enter " [/COLOR][/COLOR][COLOR=Red]cd Downloads[COLOR=Black] " hit enter

13. enter " [/COLOR][/COLOR][COLOR=Red]./mambo801.sh[COLOR=Black] " hit enter

14. the terminal may ask for admin password, then hit enter

15. the script should run, and it will ask you a few questions along the way of the install.

16. it asked for the model of my printer, for me i just entered the model number from the top of the machine ie. dcp-j125. and yep i put the dash in as thats the way it is on the machine.

17. the only question i wasn't sure on is something like "will you define the URI? y/n? " i went with the safe option and selected " n " for no.

18. finally it asked me if i wanted to do a test page. which i did and perfecto, the printer was working.

19. it then promted me to hit return/enter. do so then close the terminal window/program.

Note: at times it seem as though the program had frozen. be patient, the program only looked like it had frozen for at max 30secs before continuing. so if it does nothing for ten minutes......then yep i'd say its frozen. 

job done.
thankyou very much for your help pdc!!! i couldn't have done with out your guidance!
[/COLOR][/COLOR]

---

### Post by offgridguy on 2012-11-07
I gave up trying to install the driver for my brother DCP7030,  I may have to give it
another go with the help of this thread,  I was struggling with the same brother
web site and install script.  Thanks, I will save this in subscribed.

---

### Post by mambo801 on 2012-11-08
> **offgridguy said:**
> I gave up trying to install the driver for my brother DCP7030,  I may have to give it
another go with the help of this thread,  I was struggling with the same brother
web site and install script.  Thanks, I will save this in subscribed.

no worries, i hope it helps as many people as possible. let us know if you have a successful result.

---

