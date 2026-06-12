---
title: "[SOLVED] Shortcut to website opens in gedit"
date: 2008-08-22
forum: General Help
---

### Post by L a r r y on 2008-08-22
I created a desktop launcher, selected Location, placed the address of a web site ([http://example.com/](http://example.com/)) into the location field, gave it a name and double-clicked the resulting icon.

The page at [http://example.com/](http://example.com/) is loaded into the gedit text editor and is ready for me to view the source code.

The other alternatives to Location are Application and Application in Terminal in the launcher.

I have made such a shortcut before, and it opened with Firefox.  Rather than open the AOL Radio player in a tab each time I open Firefox, I copied the AOL Radio player address from Firefox and put it in the launcher.

But I download the page into gedit instead of starting the player in a browser window.

So I created a shortcut to my website, exactly like this:
 [http://example.com/](http://example.com/)
and have it open in gedit also.

Right-click and I see:
Open
Browse folder
______
Cut
Copy
...

Nothing here that tells me to open with..., and with the AOL link I did not have the browse folder option presented.

The Property sheets for both launchers list the location as being in /home/me/Desktop, Type is HTML Document, and MIME type is text/html.  Everything else is Unknown.

The permissions of "aolPlayer.html" could not be determined, and
The permissions of "/" could not be determined.

Notes tab is empty, and the link tab contains the respective Web address in the Location field, as in [http://example.com/](http://example.com/).

Where do I look to straighten this out?

Thanks in advance.

I am running Ubuntu 8.04 .

---

### Post by matey3 on 2008-08-22
I tried the same things but I still get Open With as the 2nd or 1st choice in the drop-down menu every time??

Have you tried holding down the Shift key then right-clicking the icons?

---

### Post by L a r r y on 2008-08-22
> **matey3 said:**
> I tried the same things but I still get Open With as the 2nd or 1st choice in the drop-down menu every time??

Have you tried holding down the Shift key then right-clicking the icons?

I just did try the Shift key, same result, but here's the kicker:

I am running a Kiwi install of Ubuntu 8.04 on a second computer, and I put the same launcher on that Desktop, and it loads the web site in Firefox, as it should.

All of my right-click menu items are the same, the Property sheet reads the same, yet it works.  I also held the Shift key in there and right-clicked with same result.

On this computer that opens the text editor, I originally started with Ubuntu 6.06 and upgraded to 8.04 online because the 8.04 Live CD never got off the ground.

I would like to use this opportunity to learn a bit more about the way Ubuntu works and see where it is that instructs the computer to take a certain action.  Do I need to look in Firefox, or is there an Admin area I should look at?

---

### Post by Alaric on 2008-08-22
Try using the application launcher setting with "firefox www.example.com" as the command (no quotes).

---

### Post by L a r r y on 2008-08-22
Alaric,
Application launcher with _firefox [http://example.com/](http://example.com/)_ worked.

In the place of example.com, I placed a copy of the link to the AOL Radio player.

Now here's another bit of information:  I dual-booted a laptop with Windows Vista and Kiwi version of Ubuntu 8.04, and it is connected via wireless to my non-broadcasting wireless network.

I brought up Ubuntu and clicked the link to the location launcher for AOL Radio, and it brought up gedit, unable to connect, because I needed to configure the network and sign in.

After I signed onto the network, I double-clicked the location launcher and up came AOL Radio in Firefox.

This [Edit]**Desktop**[/Edit] computer with the location launcher blues is connected by wire to my router.  So maybe something having to do with the network configuration?

This computer gets email when I launch Thunderbird, gets connected when I launch Firefox and ftp's when I launch the FTP client, but launches gedit when I use a location launcher on the desktop.

Your work-around solves the immediate issue, but I hope this thread answers the question of why was it necessary to perform the work-around.

Thank you!

Any ideas?

---

### Post by L a r r y on 2008-08-23
I ended up putting the application launcher on the laptop also because it would not otherwise open on the selected AOL Radio stream.  

Looking at the following partial address, which is from an Application Launcher and prefaced with the name of the program used to open it, if we eliminate the program name and just insert this address into a Location Launcher, the underlined part is not picked-up.  A default stream is played instead of the intended stream.

firefox h.t.t.p://...../aolPlayer.html_?v=new3.11.87&ur=1&us=1&id=2373_

I will call this thread solved, and thank you again, Alaric.

Reason for the edit:  I needed to get rid of link underlining which interfered with my specified underline.

---

