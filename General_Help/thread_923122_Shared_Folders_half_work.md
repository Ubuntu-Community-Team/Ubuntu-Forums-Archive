---
title: "Shared Folders half work"
date: 2008-09-18
forum: General Help
---

### Post by Bucky Ball on 2008-09-18
So, tried to figure this out and have posted some days ago but no replies so I'll try and keep it short.

Setup shared folders on my laptop and desktop both running Hardy 8.0.4. All seems to be fine with the laptop. I can see both the desktop and its shared folders on the laptop and they function fine.

The desktop sees the laptop in networks, but doesn't see the shared folder in it. 

Oddly, the shared folder on my laptop shows up fine in Windoze on my audio workstation (box #3).

Set this up about a week ago so logged in and out many times so that is not a fix.

Any and all ideas and suggestions gratefully received and thanks in advance. :)

---

### Post by amac777 on 2008-09-18
Hmm... Might need some more info. Because you mentioned Windoze, I assum you have setup all the shares using Samba. what happens when you try to browse from your desktop to the laptop share directly? For example, in nautilus on your desktop, try browsing like this:

smb://ipaddress_of_laptop/shared_folder_name

---

### Post by Bucky Ball on 2008-09-18
Interesting, but I don't need to do that to access the shared folder from my desktop on my laptop, if you follow me. It is just there in 'Places->Network->DesktopBox->SharedFolder' so see no reason why it should be any different accessing laptop shared folder on my desktop. We can leave the windoze box out of the equation. All shares are working fine on that and was just experimenting there when I set it up to see if Windoze would play the game.  :)

I will give what you are suggesting a try. The one problem with it is that because my router is serving the dhcp addresses (not static) I would have to look up the IP of the laptop everytime I wanted to access its share (if your suggestion worked, that is).

Again, there is probably a simple solution to this I am just not seeing - same os on both machines, works one way, not the other. A setting on my shared folder on the laptop? But that shows fine in Windoze.

Let you know ...

Result:
Nautilus cannot handle network: locations

---

### Post by Bucky Ball on 2008-09-18
The error message I am getting at:

smb//laptop/laptopshare

(sees the laptop so no need for IP as I suggested) is failed to mount windows share. Can see my machine fine as I mentioned in first post, just not the shared folder.

Might be as I was thinking; sharing between Ubuntu machines slightly different than a straight Windoze share so perhaps I have omitted to install something on the laptop when I set it up for sharing. Hmm. Will continue scouring for a clue. :-k

---

