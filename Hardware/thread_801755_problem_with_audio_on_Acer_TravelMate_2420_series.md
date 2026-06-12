---
title: "problem with audio on Acer TravelMate 2420 series"
date: 2008-05-20
forum: Hardware
---

### Post by sam82 on 2008-05-20
Need help on sound card from Acer TravelMate 2424NWXCi...no audio output in playing Rhythmbox player..I am a new user with Ubuntu Studio...an error in adjusting volume indicating no Gstream support...pls Help.. thanks...email add: [email]sam08_82@yahoo.com[/email]

---

### Post by nicedude on 2008-05-21
This is my new standard response to no sound issues and if it doesn't help you resolve your issues you will want to post back to your thread what you learned from these ideas so others will know that these are not your problem. This advice is designed for Ubuntu 8.04 help buts applies to other Ubuntu versions as well in most if not all respects. If you have tried any of these and say so in your thread I am sorry as this is just a way I thought of to be able to help point people quickly to some common problems I am aware of that may be stopping you from getting sound output. If any Ubuntu gurus would care to PM me with any additions or corrections I would appreciate it as I am trying to increase my knowledge of Ubuntu configuration.

1. See if your sound card device is being detected by Ubuntu. To do this open a terminal ( top menubar click Applications -then-> Accessories -then-> Terminal ) and then type the following command "lspci" without quotes and then look through the output it produces and you should see one that says audio device if not then your sound card device is probably not being detected properly and you should post this information along with lspci's output to your thread so someone can help you further as you will need to load a driver module for it at boot time and this will be device specific so someone who has done this before or is a Uber Ubuntu geek here can help. If it is listed then go to the next step.

Example of what you are looking for in the lspci output
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)

2. In case you use the alsa sound system and controls which most Ubuntu systems do check the volume levels by running the following command in a terminal "alsamixer" without quotes and verify that the master and pcm volume levels are turned up ( Thats my main ones at least but you might jsut turn everything up untill you get some sound going ). If your main or other important sound bars were muted then go to next step so you can test your sound output.

3. Have a look at the top menu bar and click System -then-> Preferences -then-> Sound. If in step 2 your sound was muted just press test on one of the test buttoms. If yours were not muted in step 2 try setting the first 4 selections to auto detect and press test to see if you now have sound, If not try setting them to alsa and try the test button again.

If none of this works please post that you tried these and also if your sound card isn't being reported by lspci ( Along with the lspci output ) so someone here can help you further but this should give them a good headstart as to what your problem is.

Hope this helps you out to get your sound going,

nicedude

---

