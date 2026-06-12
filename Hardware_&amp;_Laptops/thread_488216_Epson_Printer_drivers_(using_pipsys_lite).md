---
title: "Epson Printer drivers (using pipsys lite)"
date: 2007-06-29
forum: Hardware &amp; Laptops
---

### Post by yahooadam on 2007-06-29
Well after struggling to get my Epson Stylus Photo R265 to work on ubuntu fiesty (7.04) i decided i would write up how i got it to work

Firstly - epson seem to have outsourced their Linux drivers to another part of their company (probably to hide how cr*p they are at doing Linux drivers)

they seem to offer 2 sets of drivers
[LIST]
[*]Photo Image Print System
[*]Photo Image Print System Lite
[/LIST]

I'm going to be talking about the latter, i don't know how different the former is, if someone could inform me i would be grateful to tell people if this guide applies to both sets of drivers (which would be great)

[SIZE="5"]**Prerequisites**[/SIZE]
[LIST]
[*][The Epson drivers]("http://www.avasys.jp/english/linux_e/dl_ink.html")
[*]CUPS
[*]Alien
[*]A computer with a graphical interface (i believe you need gnome)
[/LIST]

If you want to share the printer over the network, you will also need samba

[SIZE="5"]**Alien and CUPS**[/SIZE]
This is the easy step
```
sudo aptitude install cupsys
sudo apt-get install alien
```
And your done, easy stuff

Note, if you are just compiling the drivers on your GUI computer, i don't think you need cups

[SIZE="5"]**The Epson Drivers**[/SIZE]
Here comes the oh so fun part

you need to download the drivers (i chose Debian, other on their site), this will give you an RPM, now you need to convert the RPM to a deb to install it (isn't this a great system <_<)

1) Go to the directory with the RPM in it, and then run the following command
```
sudo alien -d --scripts name_of_the_rpm.rpm
```

2) now install your freshly created deb package
```
sudo dpkg -i name_of_the_rpm.deb
```

3) Now you need to find out where your printer is
```
cd /dev
dir usb*
```

Now you should see something like "usblp0" (hopefully that's exactly what you see)

4) Now run the epson software
```
sudo /usr/local/EPAva/LITE/setup
```
When it says "Please specify the connection of a printer." you need to put in
/dev/usblp0

5) Run the Installer
```
sudo /usr/local/EPAva/LITE/pipslite-install
```
(This is the bit that requires a GUI)
Hopefully, if all goes well you now finally have the ppd file (didn't that take a while - crikey)

[SIZE="5"]**Installing the Printer**[/SIZE]
Right, now you have the PPD file you can add the printer
There are a few ways to do this, either you have a GUI installation, therefore just add a printer, and it will ask you to specify a PPD file, link to the PPD file and you are all set

You can also use the web interface
[http://localhost:631](http://localhost:631)

The epson manual also says you can do this
```
lpadmin -p printer_name -E -v ekplp:/var/ekpd/ekplp0 -m ppd_file
```

If you don't have a GUI, then your final alternative (which personally i prefer), is to open up the CUPS web interface to your network, so that you can setup the printer like that

[SIZE="5"]**Opening the CUPS web interface to your network**[/SIZE]
```
sudo vim /etc/cups/cupsd.conf
```
Under
# Administrator user group...
SystemGroup lpadmin

you need to add
```
#Allow Remote Access
Port 631
Listen /var/run/cups/cups.sock

```

and change
```
# Restrict access to the admin pages...
<Location /admin>
  Order allow,deny
  Allow localhost
</Location>

```
```
# Restrict access to the admin pages...
<Location /admin>
  Order allow,deny
  Allow localhost
  Allow put.ip.in.here
</Location>

```
The ip you should put in is the IP of the computer you are configuring from

and then finally
```
sudo /etc/init.d/cupsys restart
```
and you are done

[SIZE="5"]**Sharing CUPS printers with samba**[/SIZE]
I'm assuming you already have samba setup, if not, there are quite a lot of guides out there already - you only need a basic samba setup

Add to the [global] section
```
printing = cups               # tell samba that we'd like CUPS for printing
printcap name = cups

```

then you need 2 more sections
```
[print$]
        comment = Printer Drivers
        # this path holds the driver structure
        path = /etc/samba/printer
        guest ok = no
        browseable = yes
        read only = yes
        # add a username to the write list
        # if you don't want root to be the only
        # printer admin
        write list = username,root

[printers]      # here all printers will be shown; this becomes the Printers
                # share/section under Network Neighborhood
        comment = All Printers
        path = /var/spool/samba
        browseable = no
        public = yes
        guest ok = yes
        writable = no
        printable = yes
        printer admin = printer_username,root

```
and finally
```
sudo /etc/init.d/samba restart
```
And your done

[SIZE="5"]**Final Thoughts**[/SIZE]

Hopefully this has helped someone, your main problem (IMO) is getting the PPD file, once you have that, its not too hard to get the printer working

Hopefully, one day, printing in Linux will be as easy as running a single file, like windows

Also, please tell me if this helped you, or if it didn't, hopefully this well get most people up and printing
Also, for those with printers that support it, this did still allow me to print CD's over the network (for those that were worried)

---

### Post by holdup on 2007-07-01
Hi there,

This hasn't quite worked for me as I am on the AMD64 architecture, and hence can't convert an i386 rpm.

Has anyone tried building the drivers from the source?  I keep getting errors when I try, but to be honest I'm a relative newbie to ubuntu linux so building the drivers is new to me.

Any help suggestions greatly received.  not getting the printer working will be a bit of a show stopper for my wife, and mean I end up having to go back to Open Office on Windows just because it prints!!!

Thanks in advance

andyb

---

### Post by yahooadam on 2007-07-01
sadly avasys havent made a 64bit driver, they have said they might in the future, but i wouldnt hold my breath atm
also if you check the avasys forums, there are many complaints with compiling and 64bit

Im sorry but i dont think theres a solution (except 32bit ubuntu)
-Yahooadam-

---

### Post by holdup on 2007-07-01
Ok,

I've re-installed ubuntu but 32bit version this time.

Followed the procedure here, and have a printer that prints... kind of.

The ink was a bit low,  but mtink correctly detected that so thats cool and I replaced them.  Black is full the others are all around 50 - 90 %

I went in to gedit to print off my xorg...   fed a sheet though..... nothing on it when it came out even though it sounded like it was printing it!

So I printed a photo off in open office,  it came out but the colours werent right and the text underneath didnt print.

Any suggestions?

andyb

---

### Post by yahooadam on 2007-07-01
when you were replacing ink cartriges, did u get them all in the right way (i know it seems silly, but its easy to do)

Next i would suggest you print a test page to make sure thats ok

-Yahooadam-

---

### Post by betterspud on 2007-07-10
@yahooadam

Just wanted to say thanks. With your help I've just set up my Epson R300 with Feisty in a little over ten minutes.
Its my main printer on my XP box, which I occasionally want to use to print from my Feisty laptop. Maybe one day I'll get it set up as a network printer, but for now, using it as a local printer sinply by plugging the USB connection in is good enough... 

BTW, I'm using the full PIPS version (not lite) and it all went exactly as you said. Very happy. Thanks again...

---

### Post by mattybigback on 2007-07-21
> **betterspud said:**
> @yahooadam

Just wanted to say thanks. With your help I've just set up my Epson R300 with Feisty in a little over ten minutes.
Its my main printer on my XP box, which I occasionally want to use to print from my Feisty laptop. Maybe one day I'll get it set up as a network printer, but for now, using it as a local printer sinply by plugging the USB connection in is good enough... 

BTW, I'm using the full PIPS version (not lite) and it all went exactly as you said. Very happy. Thanks again...
I am having terrible trouble trying to get my R300 to print. I used the full driver, but I cannot reach step 5 of the install guide, because there is no installer to run. The driver is listed in the Add Printer list, but when a test page is sent it just says ERROR in the jobs section.

Any help would be appreciated!

---

### Post by yahooadam on 2007-07-21
> **mattybigback said:**
> I am having terrible trouble trying to get my R300 to print. I used the full driver, but I cannot reach step 5 of the install guide, because there is no installer to run. The driver is listed in the Add Printer list, but when a test page is sent it just says ERROR in the jobs section.

Any help would be appreciated!
because your using the full driver i dont think the path is the same

where i say
sudo /usr/local/EPAva/LITE/setup

for the full version of pipsys its going to be somthing else

also the installer bit
sudo /usr/local/EPAva/LITE/pipslite-install

the installer for the full version of pipsys is probably different (mayber pipsfull-install ?)

---

### Post by Primenumber5 on 2007-07-30
Hi there - sorry if this sounds stupid - I have been following your guide to setting up my Epson R265 and have managed to get part way through - to the point of: 5) 
'Run the Installer
Code:
sudo /usr/local/EPAva/LITE/pipslite-install'
I then get the following messsage: 'Gtk-WARNING **: cannot open display:' As you might guess I am a novice with Ubuntu so clarity is needed - any help appreciated

---

### Post by yahooadam on 2007-07-30
> **Primenumber5 said:**
> Hi there - sorry if this sounds stupid - I have been following your guide to setting up my Epson R265 and have managed to get part way through - to the point of: 5) 
'Run the Installer
Code:
sudo /usr/local/EPAva/LITE/pipslite-install'
I then get the following messsage: 'Gtk-WARNING **: cannot open display:' As you might guess I am a novice with Ubuntu so clarity is needed - any help appreciated
Are you running this on a computer with a GUI ?

It has to be run from terminal, but you muse have a gnome desktop (kde may work also)

---

### Post by Primenumber5 on 2007-08-01
Hi Yes I have a GUI - Gnome and I have been using a terminal - thats where I get this message - 'GTK warning - cannot open display'?

---

### Post by yahooadam on 2007-08-01
thats very odd, it worked fine for my on ubuntu, It however gave that exact error when i tried to run it on my server, which is headless

You did remember to run it as sudo right ?
Otherwise, at a guess i think your xorg config could be wrong ...

---

### Post by Primenumber5 on 2007-08-01
Yes - I ran it as Sudo - what do you mean about Xorg config being wrong - how do I deal with that?  your help is greatly appreciated

---

### Post by yahooadam on 2007-08-01
if xorg (the display manager stuff) was wrong and the screen isnt setup right, then the installer wont attach to it

I googled for your error
[http://www.google.co.uk/search?q=Gtk-WARNING+**%3A+cannot+open+display%3A&sourceid=navclient-ff&ie=UTF-8&rlz=1B3GGGL_enGB225GB225](http://www.google.co.uk/search?q=Gtk-WARNING+**%3A+cannot+open+display%3A&sourceid=navclient-ff&ie=UTF-8&rlz=1B3GGGL_enGB225GB225)

the first result said
> For this error, the most common cause is that you are not running the X server.
So you have to type "startx" first then retry with your application.
It also happened to me when I did a "su - anotheruser" and tried to run from anotheruser without having proper access to my $DISPLAY. I quickly solved this by copying .Xauthority from the user running the X server to the users who su to, then did a export DISPLAY=:0
However I am not sure if this is the most secure and apropriate way to do it, but it worked and no longer gtk-warning **: cannot open display:
second
> That would happen if you log in as a regular user but call firefox from a terminal as root. Is that your problem?
third
> Have you installed X11?  If not, that's what you didn't do right.

If you have installed X11, is X11 running? If not, that's what you
didn't do right.

If X11 is running, have you set the DISPLAY environment variable to
:0.0?  If not, that's what you didn't do right.

So my guess, try typing startx first, and make sure the user your logged in as is an administrator

---

### Post by Primenumber5 on 2007-08-02
Thanks for that - tried to use 'startx' then get the following - 

xauth:  creating new authority file /root/.serverauth.7046

Fatal server error:
Server is already active for display 0
        If this server is no longer running, remove /tmp/.X0-lock
        and start again.


Xlib: connection to ":0.0" refused by server
Xlib: Invalid MIT-MAGIC-COOKIE-1 key
giving up.
xinit:  unable to connect to X server
xinit:  No such process (errno 3):  Server error.


I cannot see where to start X11 - I have installed everything that has X11 in the name - sorry this is getting very convoluted

---

### Post by Primenumber5 on 2007-08-02
I have tried this in a root terminal

---

### Post by yahooadam on 2007-08-02
perhaps if you do it this way

go to terminal, stay as an administrator user (but don't sudo su - if you ever have)

then do
```
gksudo /usr/local/EPAva/LITE/pipslite-install
```

if that doesn't work, i really don't know what to suggest, I'm not a Linux genius, and this is rapidly getting out of my comfort zone :p

---

### Post by Primenumber5 on 2007-08-02
No that doesn't produce any different result - thanks very much for your help anyway - I think I will buy a new printer - this one is my home printer - I have a very nice HP colour laser at work which works a treat with Ubuntu - think I will get one of those and ditch  the Epson - once again thanks a lot for trying to help

---

### Post by holdup on 2007-11-11
Just to let people know,  R265 seems to work perfectly well once Gutsy is upgraded too!

woohoo,  might be able to go back to the AMD64bit v now.

---

