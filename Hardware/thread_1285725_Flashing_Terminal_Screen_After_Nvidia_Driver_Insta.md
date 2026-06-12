---
title: "Flashing Terminal Screen After Nvidia Driver Install"
date: 2009-10-08
forum: Hardware
---

### Post by bluejeansummer on 2009-10-08
To day I decided to repurpose an old computer laying around my room into a media center. I found the closest install disk on hand (9.10 Beta - Alternate CD) and installed. Installation went fine, and I installed the media center software, and confirmed that the internet worked over a LAN cable. I had a wireless card plugged in, but it didn't show up. More on that later.

This is where the problems began. To facilitate it as a media center, I put in my old Nvidia FX 5200 into the computer. I know the drivers work in Ubuntu, as until about 2 weeks ago, that was the card I was using. It has an S-Video port on it, and I was going to run that to the TV. Turning on the computer, the POST screen wouldn't show up unless the monitor was plugged into the onboard graphics.

Once it booted, I looked in the Hardware Drivers program to see which drivers to install. Nothing was on the list, so I decided to install it manually. With a quick [FONT="Courier New"]sudo apt-get install nvidia-glx-173[/FONT], I rebooted. That was the last time I've seen my desktop. Not only will the GUI not start, my screen is flickering, and most of my keystrokes don't register. This makes it impossible to login, much less attempt to uninstall the driver.

Is there any way I can uninstall this driver until I can get to the root of the problem? It seems odd to me that there were no suggested drivers in the Hardware Drivers dialog. I did [FONT="Courier New"]lspci[/FONT] in the terminal before I rebooted, and I believe it listed the graphics and wireless cards, further adding to my confusion.

This computer is a Dell Optiplex GX240, thin model. If necessary, I can post pictures of how the PCI cards are oddly attached inside, as they are too tall to fit in the thin case normally.

Any help with either of these two issues would be much appreciated. I'd rather not have to reinstall, but I can if all else fails. Whatever must happen, I would like to get it done quickly, as it is now sitting in the middle of my living room floor sitting next to a massive CRT, which my parents would like moved.

---

### Post by bluejeansummer on 2009-10-09
I found a solution! Thinking it might be a hardware problem (I tried reinstalling the OS and the driver with the same result), I unplugged the AGP card which I previously though was onboard graphics. Once the card was unplugged, it booted normally! I don't understand why that worked, but it did!

---

