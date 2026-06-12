---
title: "sound used to work, but it  quit on me"
date: 2007-08-07
forum: Hardware &amp; Laptops
---

### Post by Victim_of_Gluttony on 2007-08-07
i recently installed ubuntu onto my hp laptop. when i first installed it, everything except my wireless was working fine. i fixed the wireless. but at some point during the "repair" my sound stopped working. what can i do to fix this? im not even sure what my sound card is...

---

### Post by fredj on 2007-08-08
Open a terminal and type cat /proc/asound/card0/codec\#*
The first line of the output from this should tell you the name of your soundchip.
Open the alsa mixer (double click on the speaker icon). Check the File->Change Device menu
to make sure that the correct device is selected. Use the File->Preferences menu to add
all the possible volume controls and switches for both playback and record. Make sure volume
controls are unmuted and suitable levels are set.

Check System->Preferences->Sound item from the taskbar and check that you haven't
stopped sounds from playing. Also try to play the test sounds.

---

### Post by Victim_of_Gluttony on 2007-08-08
i tried all of that, and the card was not set right in alsa, but the sound is still out of commission.

---

### Post by Victim_of_Gluttony on 2007-08-08
problem has seemed to fix itself. i guess restarting isnt as effective as turning it off and leaving it over night.

---

