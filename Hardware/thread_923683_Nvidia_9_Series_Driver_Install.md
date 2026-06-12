---
title: "Nvidia 9 Series Driver Install"
date: 2008-09-18
forum: Hardware
---

### Post by Mardoct on 2008-09-18
Unfortunately I couldn't find any automated installation for my Nvidia GeForce 9600 GT, so I found a way to install it manually and get it to work with my X server.

[Get the driver here.]("http://www.nvidia.com/Download/index.aspx?lang=en-us")

(My installation assumes you rename the file "Driver.run" and put it in the '/home/UsernameHere' directory.)
 
Right click on the driver file -> properties -> Permissions -> Allow executing file as program
Get the libc6-dev package from the Synaptic Manager. If it prompts you to install dependencies, do so.

Go to Applications -> Accessories -> Terminal (Or Konsole, or any terminal.) and Enter:

> sudo init 1

This will close the X server and leave you at a screen asking what you want to do. Press the arrow keys to highlight the "root" option and press enter. Go ahead and type in:

> '/home/UsernameHere/Driver.run'

This will run Nvidia's installer Go through the steps. When it finishes, you're back at the root prompt. To finish off the installation enter:

> nano /etc/default/linux-restricted-modules-common

Change the last line to read

> DISABLED_MODULES="nv"

Press ctrl+x to save it, y to confirm and enter to finish. Now reboot the computer. (You can use the command "reboot" to do this.)

Hope this helps. Only tested with the 9600 GT driver, but I see no reason this shouldn't work for other 9 series cards.

---

### Post by Teetdiro on 2008-09-18
bump up ..Traveling salesmen make their living visiting as many customers as possible. So speeding to get from one appointment to the next is not unheard-of. Which is how I got pulled over by a highway patrolman. "Don't you ever look at the speedometer?" the officer scolded. Before I knew it, the truth spilled from my mouth. "As fast as I was going," I admitted, "I was afraid to take my eyes off the road." ------------The WOW gold Online Store, Open 24/7 Looking to buy [wow gold](http://www.u4game.com), Items or Accounts? You would find the cheapest gold here. We always online 24 hours a day, 7 days a week, any questions regarding [world of warcraft gold](http://www.u4game.com), powerleveling,wow leveling ,[warcraft gold](http://www.u4game.com), just talk to our representatives using our 24/7 live chat service.[world of warcraft gold](http://www.u4game.com/world-of-warcraft-gold.html),[wow leveling](http://www.u4game.com/Wow_Power_Leveling.html),

---

### Post by HousieMousie2 on 2008-09-29
This did not work for me... but this did:

[http://ubuntuforums.org/showthread.php?t=880787]("http://ubuntuforums.org/showthread.php?t=880787")

Not trying to rain on anyone's parade, just trying to cross link threads, since it seems like every other person's machine is different.

Thanks for the link to the driver, Mardoct!

Cheers

---

### Post by uberlube on 2008-10-11
I am not posting anything here that anyone will find of use... i am merely posting as a reference so i can try this out on my friend CPU....sorry. I tried using the latest driver in EnvyNG to get WoW working...didnt work. I kept getting that stupid memory 132 error...grrrrrrrr!!!! Will report on success though. : )

---

