---
title: "Sunbird and mobile synchronization ordeal"
date: 2008-08-30
forum: General Help
---

### Post by nostromo2 on 2008-08-30
I'm a quite green Ubuntu novice. I have spent considerable amount of time and gimmics trying to synchronize Thunderbirds Lightning extension calendar with my cell phone. There has been no success.

I read from somewhere that Sunbird has replaced .ics-files with Sqlite as a way to store calendar data and that was the reason why there were no libopensync-sunbird-plugin for Hardy yet (I belive). I got the plugin (which I believed to support Sqlite) from the Intrepid repository. Had to get also libneon27 > 0.28 (which isn't so stable, I was told) to have it to install. I used Multisync 0.82 and 0.90 as a frontends, but both produced "error while initializing syncengine:(null)".

When I tried to use ics-file in Lightning as a remote calendar on my local computer and configured sunbird-sync plugin in Multisync 0.90 to look for it from path, it said: "error while initializing syncengine:Unable to parse config data: unable to parse settings"

There must be Sunbird users who have set this thing up with Hardy. Any information and experiences are most welcome. I thank you before hand and kiss your feet.

---

### Post by Angelos72 on 2008-12-10
I got a similar message when I tried to synchronize my mobile phone with Evolution.

I figured that there was something wrong with the settings of the irmc-sync member of the group.

It's really funny I did not think of this earlier...

Under the actual configuration file, there is a whole set of instructions on how you can find the MAC address and IRMC channel of the phone. 

Apparently these instructions are not commented out and opensync tries to interpret them as settings. Naturally it's "Unable to parse settings".

To make a long story short, just delete all the instructions or anything else that should not be part of the settings (possibly between marks such as <-- ).

This should do the trick!

Let me know if it worked.

---

### Post by Angelos72 on 2008-12-10
I found what is exactly wrong.

The way to comment out something is the following:

<!-- Here I write my comment. This will not be parsed -->

Apparently, double dashes are forbidden within a comment.

So if someone makes a nice divider using dashes like so...

--------------------------------------

then what he really does is that he/she includes many double dashes "--" and gets the whole thing messed up.

Try replacing the dash separator, with a, lets say, stars (*) separator.


like so...

***********************
Now the settings are parsed as they should and you get to keep the very useful instructions.

---

