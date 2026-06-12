---
title: "install mp620 canon printer to ubuntu 10.04"
date: 2010-05-31
forum: Hardware
---

### Post by Chuck_N on 2010-05-31
canon mp620 attached to home router.
wife's computer, windows, wired direct to router. printer working fine.

my computer  presario  sr1503wm   wired direct to router.
using ubuntu 10.04 LL

I've been reading through the forum, but my situation seems different.  I'm not trying to
access the printer wirelessly.  Although I'd go that way if it's easier.....

Wired or not,  how do I install the printer?

---

### Post by Chuck_N on 2010-06-30
hi
I've waited 4 weeks for a response.  Am I doing something incorrect?

---

### Post by tgalati4 on 2010-06-30
You have the patience of a Zen Master.

I couldn't find a linux driver for the mp620.  Canon printers are not known for their compatibility with linux.

[http://cups.org/ppd.php?L+I40+T+Q](http://cups.org/ppd.php?L+I40+T+Q)

---

### Post by Chuck_N on 2010-06-30
> **tgalati4 said:**
> 

You have the patience of a Zen Master.

[http://cups.org/ppd.php?L+I40+T+Q](http://cups.org/ppd.php?L+I40+T+Q)


nah, just didn't need to use my printer 'til now.

thanks, chuck

---

### Post by tgalati4 on 2010-07-01
Send Canon an email describing your situation.  Post the response.  We all need some levity.

---

### Post by Chuck_N on 2010-07-01
okay, I will do that now.

while I do that, could you help me on this?

I am considering this purchase
[http://www.tigerdirect.com/applicati...&srkey=b528400]("http://www.tigerdirect.com/applications/searchtools/item-Details.asp?EdpNo=4312749&sku=B52-8400&srkey=b528400")

for this Compaq Presario SR1503WM

please comment on appropriateness
to replace onboard graphics
and hopefully have no more troubles with blackouts?

---

### Post by Chuck_N on 2010-07-01
> **tgalati4 said:**
> Send Canon an email describing your situation.  Post the response.  We all need some levity.

They received my email and promised a response today.......

---

### Post by Chuck_N on 2010-07-01
> **Chuck_N said:**
> They received my email and promised a response today.......

okay, here's my request:

INQUIRY: I love my MP620;  worked super and connected easily on my 
previous computer.
I  would now like to hook it up to my Compaq Presario with Ubuntu 
operating  system.  I can't find a driver on your list.  Please don't 
tell me  you don't make Ubuntu drivers, or drivers for other Linux 
products.  If so, you're missing out on a large market.
Please email reply.
Thank  you

and their response:
Dear Chuck:

Thank you for contacting Canon product  support regarding Ubuntu drivers 
for your PIXMA MP620.  We value  you as a Canon customer and appreciate 
the opportunity to assist  you.

Please know that Canon has not announced any development  plans for 
drivers or software supporting the various Ubuntu, Linux,  BeOS, or Unix 
operating systems.  We apologize for any inconvenience  this may cause. 

However, we appreciate your comments and  feedback.  On your behalf, we 
have forwarded your comments to Canon  USA through our Customer Feedback 
process. This process allows us to  capture important feedback from our 
valued customers. As we  constantly strive to improve our products and 
services, your  comments are vital to our continued success.

I hope this  information is helpful to you.  Please let us know if we can
be of  any further assistance with your MP620.

Thank you for choosing  Canon.

Sincerely,

Deborah
Technical Support  Representative

---

### Post by tgalati4 on 2010-07-01
Thanks.  I needed that warm, fuzzy response from Canon.  I like the touch at the end:  "Thank you for choosing Canon."

The nvidia 8400 is a good/solid video card.  It's a decent price as well.  You shouldn't have any problems with it.

If you want 3D acceleration, use the proprietary-driver installation tool (it should pop up automatically) and install the nVidia proprietary drivers.

It's not an open-source driver, but at least nVidia supports its products under Linux, unlike Canon.

---

### Post by pdc on 2010-07-02
Chuck;

if you read here

[http://forums.opensuse.org/english/get-help-here/hardware/411659-canon-pixma-mp620.html](http://forums.opensuse.org/english/get-help-here/hardware/411659-canon-pixma-mp620.html)

in April 2009 a user reported his MP620 worked perfectly with the MP610 drivers;

(that Canon provide, and have provided, ........... for years now ........)

so go here

[http://support-sg.canon-asia.com/P/search?model=PIXMA+MP610&menu=download&filter=0&tagname=g_os&g_os=Linux](http://support-sg.canon-asia.com/P/search?model=PIXMA+MP610&menu=download&filter=0&tagname=g_os&g_os=Linux)

Canon produce a wide range of drivers for linux: as .deb packages, as rpm packages and source files

and to power the scanner function as well;

you will see this page I link to above also has scanimage packages (for scanner)

as well as printer driver packages (for the printer function)

for ubuntu, **_download and install the common package first_**

(IJ Printer Driver version ..(debian common package)

THEN

download the deb package for the MP610

you should be able to install both when you download by using the gdebi package installer that you will be offered ..

let us know how it goes ..

If one goes to the Canon website, 

[http://support-sg.canon-asia.com/?personal](http://support-sg.canon-asia.com/?personal)

and selects any printer, folks will be pleasantly surprised how many pixma printers have .deb packages; .rpm packages and source files for linux 

How to use the website?

[http://support-sg.canon-asia.com/?personal](http://support-sg.canon-asia.com/?personal)

well you click on the button in the centre of the website that says 

> Select Category

then for the MP610 you select 

> Multifunctional printers

then it asks you to select Series

> Series

....... so select ....... Pixma ........

then the specific printer, and .. for most ... linux drivers are provided ..

---

### Post by madmoonfish on 2010-07-04
haha! was beaten to it by PDC by a day! 

The guide i followed from >[here]("http://www.nervous.it/lang/en-us/2009/04/canon-pixma-mp620-wireless-on-ubuntu/")< worked great!  just remember to use the sudo command in the terminal


PS guide says only tested on Jaunty, but works fine in koala and lynx :D


Guide also contains details to have scanner working with XSane.  If followed, remember the sudo command, and when asked for a password from the sever, just leave it blank :)

Oh, when 'sudo make install' go have something to eat, as takes ages to finish

---

### Post by Chuck_N on 2010-07-04
> **madmoonfish said:**
> haha! was beaten to it by PDC by a day! 
The guide i followed from >[here]("http://www.nervous.it/lang/en-us/2009/04/canon-pixma-mp620-wireless-on-ubuntu/")< worked great!  just remember to use the sudo command in the terminal
PS guide says only tested on Jaunty, but works fine in koala and lynx :D
Guide also contains details to have scanner working with XSane.  If followed, remember the sudo command, and when asked for a password from the sever, just leave it blank :)
Oh, when 'sudo make install' go have something to eat, as takes ages to finish



thanks  PDC  and Moonfish
I will try this out soon...........

---

