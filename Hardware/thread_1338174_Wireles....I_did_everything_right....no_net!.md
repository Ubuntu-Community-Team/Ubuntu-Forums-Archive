---
title: "Wireles....I did everything right....no net!"
date: 2009-11-26
forum: Hardware
---

### Post by Cytochromec on 2009-11-26
Ok, so I broke my first install of Linux (I wont get into it), but I bring that up because I had this very wireless adapter working fine and dandy. I had no idea what I was doing and ironically fixed it then, and now that I have a better idea of what I am doing I can not get it to work. Here is what I did:

1) Downloaded the right 64bit Vista drivers that I got to work last time (Im on Ubuntu 9.10 64bit)

2) Extracted the proper .inf and .sys files I needed from the windows driver package.

3) Successfully installed the following packages in the order mentioned using the command sudo dpkg -i [name.deb]

ndiswrapper-common_1.54-2ubuntu1_all.deb
ndiswrapper-utils-1.9_1.54-2ubuntu1_amd64.deb
ndisgtk_0.8.4-1_amd64.deb (UI front end I believe) 

4) Used the UI to locate and install the .inf

Now, according to this screen capture [ATTACH]137654[/ATTACH] I have the wireless adapter installed and recognized, but I have no wireless networks detected. I click configure and it doesnt work. Please note, I am a total newb, so Im sure I missed something obvious (hopefully). Help would be appreciated, thanks.

EDIT: the topic typo was....um, intentional :)

---

