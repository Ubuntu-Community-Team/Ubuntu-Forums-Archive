---
title: "Greyscale printing (Canon MG6150)"
date: 2011-02-26
forum: Hardware
---

### Post by Silvo on 2011-02-26
Hi,

I have a Canon MG6150 printer connected wirelessly to the LAN. I installed the Linux drivers from the Canon site, and they are working flawlessly (except the scanner drivers, but that's a problem for another day), except I am noticing a distinct lack of customisable options in the Printer Properties menu. 

In particular, the Color Model is fixed at RGB. Now, I print almost exclusively in black and white, and would be super-annoyed to have to waste the colour ink needlessly. 

So, is there any way of fixing this? I'm a little scared at modifying the driver to add that option, I imagine that would be very complicated. I'm thinking either there might be some open-source drivers somewhere that I don't know about, or perhaps there is a way of adding some sort of custom printer to the print menu that first converts the document to a black and white PDF before printing to the Canon.

Does anyone have any ideas? 

Thanks.

---

### Post by Yann2 on 2011-03-18
Ohhh. So this is not me being stupid, other people actually do have the same problem :) Did you get it sorted?

---

### Post by Silvo on 2011-03-18
Sadly, no, not really. I did some googling, and found some info about how to edit the config file to add the option, but I could never get it to work.

I ended up using an annoying hack to get it to work. I wrote a script that monitors a particular folder looking for PDF files, and when it finds one, it converts it to a greyscale PDF and then prints that. So, rather than printing say a webpage to the Canon, I have to print it as a PDF, which then converts and prints it to the Canon. Not in any way ideal, I know, but it's the best I could come up with. I can send it to you if you like.

---

### Post by acidUF on 2012-03-07
You can try this method:
Go to printer -> properties -> Job options -> add new option in Other options 
name: CNGrayscale
value: true

Hope it helps. I found this solution searching some other forum which I don't remember, so I cannot give the credits.

---

