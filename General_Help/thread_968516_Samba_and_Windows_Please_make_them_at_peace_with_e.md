---
title: "Samba and Windows: Please make them at peace with each other"
date: 2008-11-02
forum: General Help
---

### Post by anil_robo on 2008-11-02
Hello all I am returning to Ubuntu after many years, and am happy to see many improvements. However I have run into a problem now.

This is what I want to do:
1. Install Ubuntu on a desktop (done)
2. Install Samba on it (done)
3. Share one of the HDDs on the Ubuntu box with all the other computers on the local network and give them read/write access to the entire HDD (not done).

Ubuntu is intuitive, so I tried my intuition. This is what I did:
- Right click on the HDD and look for any sharing options. Result: No sharing options available when I right click on a drive.
Okay, geekery into action now. I went into the /media folder, found the HDD there and right clicked on it. Finally found the sharing option. Isn't this funny? Shouldn't I be able to find sharing options when I right click on the drive icon placed on the desktop??

Anyway I allowed sharing by checking "Share this folder" and "Allow other people to write in this folder". Now I go back to my Windows XP Pro box and am very happy to see the new folder I just shared listed under "my network places"

Yay!

But when I click on it, it asks me for a username and password. I enter my Ubuntu username and password, hit enter. The box comes up again, this time it reformatted my username as \UBUNTU\username. I enter password again, hit enter, and the same box keeps coming.

What the heck? Why doesn't it work the way it should?

Hours ago, I got filesharing to work by playing around with smb.conf file, but how can we expect an average user to do it on their own? Ubuntu must aim for a software "that just works" without having to play with all the configuration files and terminal commands. This is what I think.

Now can someone tell me how to enable drive shares without using scripts, configurations or terminal commands? A simple click-click-click way? Thanks a ton!

---

