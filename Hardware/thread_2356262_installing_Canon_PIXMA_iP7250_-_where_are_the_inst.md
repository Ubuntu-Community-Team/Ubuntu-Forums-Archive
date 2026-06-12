---
title: "installing Canon PIXMA iP7250 - where are the instructions on the canon website?"
date: 2017-03-21
forum: Hardware
---

### Post by ronjjjg8885 on 2017-03-21
do i have to go through all of that?
[https://www.howtoforge.com/how-to-install-a-canon-printer-on-debian-and-debian-like-systems](https://www.howtoforge.com/how-to-install-a-canon-printer-on-debian-and-debian-like-systems)

or what?

will my printer also work with wifi on linux?

---

### Post by oldrocker99 on 2017-03-21
It does look like you do have to go through all that. Some printers are a snap to install, like my Brother, and some are a major pain to install, and it looks like you have a major pain. It isn't all that difficult, and you'll have a working Wi-Fi printer, hopefully.

---

### Post by pdc on 2017-03-21
can I suggest an alternate; that should be easier ...........
____________________

[SIZE=4]**A**[/SIZE] firstly, I have edited my reply to say I now see you asked about wifi: here is what I think is a good guide from UK Canon about setting the printer up to print wirelessly

[http://www.canon.co.uk/support/consumer_products/pixma_printer_wireless_connection_setup/ip7240_printer_wireless_connection_setup/](http://www.canon.co.uk/support/consumer_products/pixma_printer_wireless_connection_setup/ip7240_printer_wireless_connection_setup/)

If you do that first; before we talk about drivers: so have a hunt on your router for the magic button you should push; to drop the protection temporarily; to allow the printer to talk to the router; ...... so ..... all good now ?? ........... 

______________

[SIZE=4]**B** [/SIZE]Canon supply drivers for printers younger than about 10yrs, so one starts here [http://support-asia.canon-asia.com/?personal](http://support-asia.canon-asia.com/?personal) to look; but if I save you the time and give you some commands to paste into a terminal? (You open a terminal with three keys held down   control alt t )

If you click on this link to Canon's Asia site for your 7200 series printer; [http://support-asia.canon-asia.com/contents/ASIA/EN/0100465502.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100465502.html) and click to download and **SAVE** the file which is [COLOR="#008000"]cnijfilter-ip7200series-3.80-1-deb.tar.gz[/COLOR]

....... *by default, saved files that are downloaded should end up in your [COLOR="#0000FF"]Downloads[/COLOR] folder *........

then into the open terminal, please paste

```
cd Downloads
```         ..........hit the ENTER key after each paste .....

```
tar -zxvf cnijfilter-ip7200series-3.80-1-deb.tar.gz
```

```
cd cnijfilter-ip7200series-3.80-1-deb
```

....... now we are ready to run the install script ....... maybe make the terminal window up to fullscreen; the script will ask some simple questions.........we assume this will be the only printer connected; and it will be usb? .. if network, you will need to already be connected to your network ..

so let's run the install script ```
sudo ./install.sh
``` and all should be good;

__________________

that link you found was what is technically called "a shocker": it is really old ...... it is about a different printer driver .. for a laser printer, not an inkjet  ........... about converting the package from rpm to deb ....... goodness ....... Canon now supply that driver in both 32 and 64bit debian packages; with an install script just like is quoted above: some of these old posts would ideally be removed but they linger to haunt and terrify newcomers: _**don't read old posts ...........!!**_

---

### Post by ronjjjg8885 on 2017-03-21
i don't understand how to use the router button and when pdc

also

i don't get any options after the > sudo ./install.sh



---

### Post by pdc on 2017-03-21
1) can you tell us the name of your router please?

____________
this is the sort of thing you are looking for: 3rd image down ..........[http://www.coolsmartphone.com/2011/11/29/three-wifi-router-review/](http://www.coolsmartphone.com/2011/11/29/three-wifi-router-review/)
__________________________________________________

I see I pasted in the instructions for the 7240 ..... must be the same as the 7250 but here is the Canon 7250 [http://www.canon.co.uk/support/consumer_products/pixma_printer_wireless_connection_setup/ip7250_printer_wireless_connection_setup/](http://www.canon.co.uk/support/consumer_products/pixma_printer_wireless_connection_setup/ip7250_printer_wireless_connection_setup/)

2) [SIZE=4]**"i don't get any options after the sudo ./install.sh"**[/SIZE]              ......... can you please ```
cd Downloads/cnijfilter-ip7200series-3.80-1-deb
``` and then the command is ```
ls
``` and that asks the computer to LIST what is in that directory; if you can copy and paste back what is there please ........ please use the EDIT button at the top of the terminal; (or copy in the terminal is shift control c .............whereas in most programmes it is control c)

---

### Post by ronjjjg8885 on 2017-03-21
i've this:
$ ls
install.sh  packages  resources


you know what?
i forgot that my printer can't communicate with the router because of a big distance
i will connect it with a usb

but im still not sure why i don't have the printer listed when i choose 'print' in chromium

edit:
i think that now it is listed after i connected the cable

edit:
it is working
would it also print hebrew?

---

### Post by pdc on 2017-03-21
your printer should print whatever is sent to it by the computer

---

### Post by bayouoldguy on 2017-05-13
Thank you pdc for the reminders. I needed to install a new Canon Pixma TS6020 printer to my old Dell  D620 laptop . Canon had the drivers on their web site.  I followed your basic command prompts using the proper Canon ID, & after a password prompt, I am up & printing on the old laptop. I have not used, command prompt in a while, so it was interesting. Thanks again, system works...."G"

---

### Post by pdc on 2017-05-14
well done; glad to help you; I think the TS6020 now uses the cnijfilter driver that seems to cover all of their printers now;

---

### Post by ronjjjg8885 on 2017-07-15
i've another problem
after installing the driver on my desktop computer the printing quality is not precise.
some letters are blurred out.

i can attach a photo if you like

---

### Post by ronjjjg8885 on 2017-07-23
anyone?

---

### Post by deadflowr on 2017-07-23
> i can attach a photo if you like
I like.
or please do, maybe it can help.

---

### Post by ronjjjg8885 on 2017-07-28
look at the top

[https://ibb.co/i8oRQQ](https://ibb.co/i8oRQQ)

---

