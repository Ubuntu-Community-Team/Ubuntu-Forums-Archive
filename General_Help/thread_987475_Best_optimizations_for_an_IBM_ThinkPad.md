---
title: "Best optimizations for an IBM ThinkPad?"
date: 2008-11-19
forum: General Help
---

### Post by MobileDev on 2008-11-19
Hello everyone. I haven't been to this forum in a long time. After hours of searching these forums and the web, and a lot of other forums, and a few a books, I'm finally posting my questions here in this forum. If someone has already asked these questions before, I appologize.

The following pertains to an old laptop and Ubuntu 8.10

I have a refurbished IBM ThinkPad R51 with an Intel Pentium M 1.6GHz processor, 512MB or RAM, Intel 82852/855GM integrated graphics, (no idea what it is, but it runs Compiz fine) and a 40GB hard drive with Windows XP Pro and Ubuntu 8.10

I have already done everything I know how to do to boost performance. Right now, I am running XFCE 4 and Compiz as my default session. I would like to know how I can cut down on my memmory usage. Right now, I am using 276MB of RAM. I need to get that as low as I can so I can somehow run MS Office 2007 because I need it for school. My two options are:

a. Somehow getting MS Office 2007 to run on Ubuntu through WINE, preferably from its current location on my WinXP partition

b. (may not be possible) Somehow convert my current WinXP installation into a virtual disk image (or whatever its called) so I can run WinXP in VirtualBox or another virtual machine. 

c. Install WinXP within a virtual box, possibly from an ISO file, and then install MS Office 2007 all over again

I **REALLY** hate working in windows, I want the whole house :lolflag: 

Also, another problem I am having is that visualisations and movies fail to display at all when Compiz is running (tried in GNOME, XFCE, and KDE). When I want to see a visualisation while playing music or when I want to watch a movie, it only displays when I have the mouse button pressed down in a specific area, and only when it feels like displaying. Is there something I can change in my xorg.conf file or in some other config file that can make these things display propperly? Tried on Totem, MPlayer, and VLC without luck. Doesn't seem to affect Flash movies or games. 

Further more, when I play armagetronad, all of the text is mangled and unreadable. I would very much like to fix that. 

Another thing that bothers me (this may have already been asked before) is the subject of wireless broadband cards from AT&T, Sprint, and Verizon.
Is there a list of compatible devices from these service providers that will work on Ubuntu or any other Linux distribution? Are there any howto guides out there that actually work? I will only subscribe to one of these providers if they have a device that will work on my laptop.

I would like to be able to connect to the net from college and, surprisingly, there are no wireless access points on campus, despite the fact that the college I am currently attending is a so-called "technical college". :confused: 

Other then the above problems, I am really enjoying the new Ubuntu. It ROCKS! :guitar:

---

### Post by kestrel1 on 2008-11-19
Why do you need to run Office 2007? OpenOffice 3 is out now & it is a great improvement on 2.4.1
I assume the reason for using MS Office is for such things as Access & Publisher which are not covered by OO 3, but Word, Excel & Powerpoint are all covered by Writer, Calc & Impress.
I work in a school & I expect you are told to use MS because that is what the teachers know. They really should look further than the MS logo, but they are a stubourne lot. :)

---

### Post by kerry_s on 2008-11-19
suck it up, if you have windows use it, do your homework with the tools they tell you to use, so the display comes out right, get your A+ and be happy.

don't play with something as important as compatibility, i've seen things done in openoffice that look totally different in msoffice. they won't care if you used a alternative office suite, they only care that it looks right on what they use.

it's up to you.

---

### Post by MobileDev on 2008-11-20
Actually, you got it wrong. One of the so-called "core curiculum" classes that I am taking right now is Advanced Spreadsheets with Excel 2007. That's the main reason why I need MS Office 2007. I know all about OpenOffice, and I prefer using it, but the morons in charge of this particular college are thinking about mandating the Office 2007 file formats. If this happens, then none of the instructors will accept anything other then Office 2007 file formats. OpenOffice can not currently save in these formats

On another note, I would really like someone to help me with the Compiz problem I described in my earlier post. I would also like to reduce my RAM usage and keep my Compiz desktop if at all possible.

---

### Post by eternalnewbee on 2008-11-20
> I know all about OpenOffice, and I prefer using it, but the morons in charge of this particular college are thinking about mandating the Office 2007 file formats. If this happens, then none of the instructors will accept anything other then Office 2007 file formats. OpenOffice can not currently save in these formats
Can't Office 2007 open these formats?
EDIT: Never mind the cursor.

---

### Post by MobileDev on 2008-11-20
OpenOffice can save in MS Office formats up to 2003, and the current version 3 can open Office 2007 formats, but it can not save anything in these newer (and bulkier) formats.

By the way, eternalnewbee, I am curious about your desktop in the attached thumnail. What desktop environment is that and how much RAM are you using? Looks like gnome but with different menu button. Custom XFCE setup?

---

### Post by MobileDev on 2008-12-07
I'm hoping this thread hasn't gone dead. I figured out how to use VirtualBox to run Office 2007. With the guest additions installed, it really works smoothly, after about 5 minutes or so. Anyway, how can I lower the RAM usage? It's making heavy use of the swap partition, which slows things down. Also, has anyone gotten Compiz to run without a full blown desktop environment? I'm doing some experimentation with FS-panel and idesk. So far, it isn't going very well. Also, LXDE is heading in the right direction, as it isn't a resource hog, but it still needs a little polishing for everyday use. Is there a way to make the LCD backlight stay at minimal brightness when running on battery power? Whenever I move a window or start a program, the screen goes back to the half brightness setting. It's really annoying.

---

### Post by kestrel1 on 2008-12-08
Whats the spec of the machine that you are running VBox on?

---

### Post by eternalnewbee on 2008-12-09
> By the way, eternalnewbee, I am curious about your desktop in the attached thumnail. What desktop environment is that and how much RAM are you using? Looks like gnome but with different menu button. Custom XFCE setup?
Hi MobileDev.
Sorry for my very late reply.
I run Gnome with Emerald. The icon theme is called Mashup. You can find it at [www.gnomelook.org](www.gnomelook.org)
I use 512 RAM

---

