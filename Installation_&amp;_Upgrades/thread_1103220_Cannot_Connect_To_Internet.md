---
title: "Cannot Connect To Internet"
date: 2009-03-22
forum: Installation &amp; Upgrades
---

### Post by Kensoi on 2009-03-22
Hi. I Am Totally New To Ubuntu. I Am Trying To Connect To The Internet & I Am Receiving The Following . Can Anyone Help? Thanks.

---

### Post by Bucky Ball on 2009-03-22
Welcome and hi.

Try going to System->Administration->Network, type your password to unlock, choose your wireless connection and hit properties.  You will need the WEP key for the router and the name of the network to connect which goes in the ESSID field. Set to 'Auto DHCP' in that window also. You will notice in the ifconfig results you posted that 'Access Point - Not Associated' and the fact you have not been given and IP address are the problems. Also, Essid - " nickname " should be the name of your network.

You may need to explain your setup a little more specifically (always try to include OS version and whatever helpful details you can think of, including a descriptive title like the one for this thread), but try this first. 

What version of Ubuntu are you using?

---

### Post by Kensoi on 2009-03-22
Hi & Thanks. 8.04 Version. I Will Try What You Mentioned Etc.
It's My First Time On Here & I Have Spent Alot OF Time Trying To Suss It Out Etc. As I Said It't The First Time I Have Had Ubuntu.
So I  Am On My Way Out Now. Really Appreciate The Help.

---

### Post by Bucky Ball on 2009-03-22
You're welcome. Should be simple enough to fix. Let us know how you go. :)

---

### Post by Kensoi on 2009-03-22
Cheers. It's My Wifes New Netbook With Ubuntu 8.04  We Chose To Go Down This Learning Path With Ubuntu. 

I Had Already Done What You Mentioned But I Still Don't Get Anything. 

I Am Wondering If It Because I'm Trying To Connect To A WPA Enabled Router ?  Netgear (DG834G) [https://help.ubuntu.com/community/WifiDocs/WLANHowTo](https://help.ubuntu.com/community/WifiDocs/WLANHowTo) It Seems There Is Not A Page Created For WPA Yet. So I'm Wondering If This Is Possible ?

---

### Post by Kensoi on 2009-03-24
Hi. I Tried The Instructions You Gave. 

I Still Have The Same Problem.

Is It A Router (Netgear D834G) Problem IE: The Mini IS Not Registering In The Router ? & When It Does Is That What Gives Me The Nickname ? 

I'm Now Thinking Of Trying To Put These In Mannually.

Thanks

---

### Post by Bucky Ball on 2009-03-24
You need to find the IP address of your router (usually 192.168.0.1 or in the manual), open up a web browser, put that number in the address window, ***not*** a search engine, and that should open the GUI to configure your router. In there, find your wireless settings. Put in an ESSID of your choosing and a WEP key (or some other kind of security but WEP is fine, hexadecimal) then repeat the instructions I mentioned earlier.

Use the data you have just setup on your router so your computer matches. Whatever ESSID ('Nickname' in your terminal post) you give the router is the name of the access point (or AP). As long as your computer matches that and has the correct security key (WEP key), you should be good to go, unless you have some other problem not related. When you run iwconfig, you should be seeing 'YourAPName' instead of 'Nickname'. When you do, you are (probably) connected.

Good luck. :)

---

### Post by Kensoi on 2009-03-24
Hi & Thanks For That. Really Appreciated.

As Your Probably Aware Finding Time Can Be A Problem !

Bit More Info: The Router I'm Trying To Connect To Is Running A Desktop Windows xp Machine. As I Said Before Ubuntu Is A Different Ball Game. Getting Used To The Layout & Command Structures Etc. 

It's Alot To Take On Board After Working With Windows For Years.
Also All These New Terms Etc.

Thanks Again
               Ken

---

### Post by Bucky Ball on 2009-03-24
> **Kensoi said:**
> 

Bit More Info: The Router I'm Trying To Connect To Is Running A Desktop Windows xp Machine. 

There are a few ways of going about it, but try this. Get into the router config using that machine (IP in a web browser) and set up the wireless. Reboot your Ubuntu machine with the correct details in System->Admin->Network.

In other words, set up the Ubuntu machine with the ESSID and WEP, set to Auto DHCP, save, shutdown. Open the router config, put the same details in there for your wireless setup, reboot the wireless computer and see if it gets served an IP from the router.

In the router, you need to make sure the DHCP server is enabled. If you are connecting with your Windows box, that is probably already enabled. Is the windoze box wired or wireless? Sorry if you already mentioned that.

I know what you mean but after using Windoze for years and being addicted to Linux for about a year and a half all I can say is ... I love Ubuntu! (esp. Xubuntu) Once you start getting used to it and the mindshift involved, you will probably find it is more straightforward. :)

---

### Post by Kensoi on 2009-03-24
Hi & Thanks. Just To Say I'm Up & Running :D . As This Was My First Experience On This Forum & Ubuntu It Has Been Welcoming & Also The Information You Gave Very Usefull.

So I'm Now Looking Forward To Exploring Ubuntu As It Has So Much To Offer & It Is A Pleasant Change.

All The Best.
              Ken

---

### Post by Bucky Ball on 2009-03-24
Good news! My pleasure and post again if you hit a ](*,) If you have been using Windows for years and you managed to get your network running through the terminal, you are going to find Linux well flexible in comparison. So customisable, I love it.

Have fun and welcome to Ubuntu! Hope you enjoy ... :)

---

