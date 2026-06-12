---
title: "Wireless hardware button to trigger event on computer?"
date: 2013-12-19
forum: Hardware
---

### Post by Pithikos on 2013-12-19
Is there some kind of device with one or a few buttons that can communicate wireless with the computer or at least just send a single signal?
I want to use this in-house to make a diary with the times I eat. Ofcourse I could use a smart mobile but unfortunately I don't have one.
So is there something small enough to fit in my pocket which can communicate somehow with the pc wireless?

---

### Post by tgalati4 on 2013-12-19
Using the journal *zim*, you can insert the time and date with Control-D.  So you would have a PC running with zim as the active application.  Now you need an application that can send a signal and use a hot-key or a script to send a Control-D to zim.

I had an older Sony phone (w810i) that had an infrared port and an application that would act as a remote control for powerpoint or music player applications.  It work pretty well.  You would need an infrared receiver on your computer for this to work.  What kind of phone do you have?

Otherwise, you would need a phone with at least wifi to be able to communicate over the network.  Bluetooth has too short a range to be practical (33-feet).

A 79-cent pocket notebook and short pencil seems to be the tool to use here.

You could set up anyremote or IRDA utilities and grab a surplus TV remote control and use that.  It would require some programming.  This is a super-old tutorial, but it gives you the general idea:  [https://help.ubuntu.com/community/IrdaHowto](https://help.ubuntu.com/community/IrdaHowto).

Anyremote is a more generalized, remote-control protocol.  [http://manpages.ubuntu.com/manpages/precise/man1/anyremote.1.html](http://manpages.ubuntu.com/manpages/precise/man1/anyremote.1.html)

That notepad looks attractive.  And it comes in different colors!

---

### Post by Pithikos on 2013-12-20
> **tgalati4 said:**
> Using the journal *zim*, you can insert the time and date with Control-D.  So you would have a PC running with zim as the active application.  Now you need an application that can send a signal and use a hot-key or a script to send a Control-D to zim.

I had an older Sony phone (w810i) that had an infrared port and an application that would act as a remote control for powerpoint or music player applications.  It work pretty well.  You would need an infrared receiver on your computer for this to work.  What kind of phone do you have?

Otherwise, you would need a phone with at least wifi to be able to communicate over the network.  Bluetooth has too short a range to be practical (33-feet).

A 79-cent pocket notebook and short pencil seems to be the tool to use here.

You could set up anyremote or IRDA utilities and grab a surplus TV remote control and use that.  It would require some programming.  This is a super-old tutorial, but it gives you the general idea:  [https://help.ubuntu.com/community/IrdaHowto](https://help.ubuntu.com/community/IrdaHowto).

Anyremote is a more generalized, remote-control protocol.  [http://manpages.ubuntu.com/manpages/precise/man1/anyremote.1.html](http://manpages.ubuntu.com/manpages/precise/man1/anyremote.1.html)

That notepad looks attractive.  And it comes in different colors!

Thanks for the answer. The thing is that the software is no problem. As long as I can get a wireless communication, I can make scripts or whatever.

Doesn't the infrared need optical reach? Because then it's impossible to use it as I will be around the house and my computer will be stationary in one room. Notebooks are out of the question as well because of the hassle. I want something small that I can have always with me.

I found something that looks a bit of what I have in mind: [http://www.alibaba.com/product-gs/1520400643/1ch_mini_12v_wireless_remote_control.html?s=p](http://www.alibaba.com/product-gs/1520400643/1ch_mini_12v_wireless_remote_control.html?s=p)

So I want that type of thing. The only problem with the one above, is that I have no idea how to connect that to my computer.

I found this on ebay also which is similar to what my wireless logitech keyboard uses: [http://www.ebay.com/itm/Wireless-USB-Mini-WiFi-802-11N-Network-WLAN-Network-Adapter-Dongle-w-WPS-Button-/150967857059?pt=UK_Computing_USB_Wi_Fi_Adapters_Dongles&hash=item232662afa3](http://www.ebay.com/itm/Wireless-USB-Mini-WiFi-802-11N-Network-WLAN-Network-Adapter-Dongle-w-WPS-Button-/150967857059?pt=UK_Computing_USB_Wi_Fi_Adapters_Dongles&hash=item232662afa3)

So I would like to have the controller from the first link and the receiver from the second and an easy way to program those buttons. Does something like that exist?

---

### Post by tgalati4 on 2013-12-20
Those are garage-door openers.  They are quite cool though, and you only need to order 100 of them.  If your computer has a serial or parallel port, then you could hook up one of those to the pins and have software read the state of the pins (open or closed).

The second adapter is a Wireless N adapter that plugs into your USB port.  How would you talk to it?  You need a smart phone with wifi to be able to talk to it.

I pulled out some old Sony Ericsson phones that I had.  They both have bluetooth with remote control capability that I have gotten to work on Mac OS X and linux, but limited by bluetooth range (33 feet max).

Notebook and pencil.
Good for logging when I eat.
PC:  Overkill.

---

### Post by 1clue on 2013-12-21
Option 1:  irDA
You might have an irDA port built-in to your computer, but if you don't then you can buy a USB irDA port for around $25 USD.  Then you'll probably have to do some research to hook it up to Linux.  Not sure if that kernel module is enabled in Ubuntu or not, I don't use them.

Then you'd be able to use whatever standard remote you wanted I think.  You probably have a few orphaned remotes sitting around in a box somewhere.

Example:  [http://www.amazon.com/dp/B004GED7SI/ref=asc_df_B004GED7SI2889628?smid=A36K7LZ3H1W18W&tag=nextagusmp0359661-20&linkCode=asn&creative=395129&creativeASIN=B004GED7SI](http://www.amazon.com/dp/B004GED7SI/ref=asc_df_B004GED7SI2889628?smid=A36K7LZ3H1W18W&tag=nextagusmp0359661-20&linkCode=asn&creative=395129&creativeASIN=B004GED7SI)

Option 2: Wifi
You almost certainly have wifi on your pc so if you can find a handheld gadget that can log into your wifi network and ping your computer then you can do it that way.  This is almost certainly going to be the most expensive option, including buying a smart phone.

Example:  Raspberry Pi + wifi + battery?

Option 3: Pure hardware
Put a lock on the refrigerator, store the key on your PC.  In order to "check out" the key, you need to start your timer.  In order to "return" your key, you need to stop the timer.

The "key" could be any token, as long as you are strict with your behavior with regards to its use.

If your goal is dieting for weight loss rather than some other reason (speaking from personal experience here), then this option might be the best in that it requires extra effort before you can get food.  That extra effort involves recognizing the need for the key, the time spent walking to the computer and then returning, all of which time you ponder the fact that the idea is for you to eat less often.  So you get a chance to "undo" before you start.  Likewise, if your "key" is big and bulky and you require yourself to hold it in your hand as you get the food, then you leave yourself with one less hand with which to get food.

Option 4: Rock paper scissors.
Tape a piece of paper on the refrigerator, hang a pencil from the refrigerator handle with a string.  Check the box or put in the time when you open the refrigerator.

This option clearly lacks any way to observe statistical behavior without data entry, but it's gotta be the cheapest way.

Option 5: Smart phone.
I'd say this is hands down your technically best option.  You can get one for free if you're past your contract date on your existing phone.  You can handle it in several ways:
[LIST=1]
[*]Have the whole timer as an app on the phone.  Gotta be dozens or hundreds in whatever app store you wind up using, some specific to your purpose.
[*]Have the phone ping the PC with some sort of request from your custom server.
[*]Have the phone ssh to your PC and perform action on a file, no server other than ssh.
[*]Have the phone ssh to your PC and run a script in your ~/bin directory.
[*]Put some sort of bluetooth device on your refrigerator, set up a proximity sensor on your phone and every time you go to the kitchen it marks you down as having ate something.
[/LIST]

---

