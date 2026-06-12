---
title: "Getting grub error 15/22 when creating another partition out of free space"
date: 2009-01-08
forum: Installation &amp; Upgrades
---

### Post by seemanta on 2009-01-08
Hi,

In my hard disk, I have 3 partitions for Ubuntu, in addition to Vista partitions and some free space:
[Windows Vista Partitions] 
[ Free Space ]
**/dev/sda5 - swap** ----\
**/dev/sda6 - /**-----------|--- [COLOR="DarkRed"]Ubuntu Installation[/COLOR]
**/dev/sda7 - /home**---/

As you can see, I have some free space before the swap partition which I want to create into another partition, accessible from both Vista and Ubuntu.

My problem is, when I create a new partition using Ubuntu Live CD, *that* becomes /dev/sda5 and swap becomes sda6 , / becomes sda7 and /home becomes sda8. Basically the drive device names get shifted by 1. (I am unable to create a new partition using the Vista disk management software anyway).

This drives grub crazy and it refused to boot, with an error code of 15 or 22.

Can you please help?   Is it possible to :

[B]1. Boot using the Ubuntu Live CD, create a new partition using Partitioner, thereby screwing up the device names, albeit temporarily until step 2 completes.

2. Reboot now using the Ubuntu live CD again(since grub won't work anyway due to step 1) and then re-install grub so that it becomes aware of the new partition device names now?[/B]

Step 2. is what is confusing me and I would proceed with the above only when I am assured that step 2 is doable.

And yes, I have Vista at the beginning, and I don't want to disturb that at all. It should not be aware that any such thing happened at all.

Thanks in advance!

regards,
Seemanta

P.S. My Vista already has 4 primary partitions, so assuming step 2 works, will creating 'another' extended partitions using the Ubuntu Live CD partitioner, make my system unbootable into Vista?

---

### Post by 73ckn797 on 2009-01-08
The grub errors are because of the inserted partitions. You would have to edit the grub to redesignate drive locations. You could try Super Grub Disk but that does not always fix things. It at least does allow you to edit grub on the fly. You can also edit grub through the grub start screen when all the OS choices are displayed.

I seem to have read something about a limit on how many partitions you can have on a single drive. You will have to search for that info own your own.

---

### Post by seemanta on 2009-01-08
Problem is, even the initial grub screen does not come up when the new partitions are inserted ! :(

What if I used the Ubuntu Live CD to get a command prompt, then I mount the new / filesystem, which would be /dev/sda7 now, change the menu.lst file in /boot to reflect the new partition names ? 

Will that work? Or reinstalling grub is the only way, if at all ? Can you point me to some info on how to re-install grub ?



regards,
Seemanta

---

### Post by cash191 on 2009-01-08
Why Easy Forex™?Now Join for Free & Making Billionaire by happy in dollars.

>>Start trading with as little as US$100

>>Credit Card use for instant Deposit

>>Guaranteed Stop-Loss Rate

>>Freeze the Rate you see (Freeze&Trade)

>>No hidden costs, Competitive spreads

>>Special Terms for frequent traders

>>No download of software

>>Live Quotes, real-time

>>Free $50,000 Practice Account With Real-Time Charts, News & Research,One on One Trainnig.

>>Who is Domain registrant?

[http://www.verio.com/whois/whois_results.cfm?fuseaction=whois_results&domain=easy-forex.com](http://www.verio.com/whois/whois_results.cfm?fuseaction=whois_results&domain=easy-forex.com)


>>Your tracking link for promoting Easy Forex™ is:(Free Joins & Free Registrations)

[http://ads.easy-forex.com/Gateway.aspx?gid=87792](http://ads.easy-forex.com/Gateway.aspx?gid=87792)

---

### Post by caljohnsmith on 2009-01-08
Seemanta, in order to get a clearer picture of your setup, how about opening a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your problem might be.

---

### Post by seemanta on 2009-01-08
Hi caljohn,

Thanks for the script. But I am not sure if I should sudo a bash script just like that off the forum. No offence to you and meierfra(and thanks a ton for taking time out to write that script), but I am not too comfortable in going to a seemingly random site and running a script as *root*. I am sure others including you two would agree with that.

I saw [another thread]("http://ubuntuforums.org/showthread.php?t=1032265") on this topic where you have asked the forum admins for their view. Unfortunately that discussion did not produce any conclusive result.

If the forum admins volunteer to check that script and upload it here, I would be the first one to use it. 

Unfortunately I am not that well versed in bash otherwise I would volunteered :(

regards,
Seemanta

---

### Post by 73ckn797 on 2009-01-08
> **seemanta said:**
> Hi caljohn,

Thanks for the script. But I am not sure if I should sudo a bash script just like that off the forum. No offence to you and meierfra(and thanks a ton for taking time out to write that script), but I am not too comfortable in going to a seemingly random site and running a script as *root*. I am sure others including you two would agree with that.

I saw [another thread]("http://ubuntuforums.org/showthread.php?t=1032265") on this topic where you have asked the forum admins for their view. Unfortunately that discussion did not produce any conclusive result.

If the forum admins volunteer to check that script and upload it here, I would be the first one to use it. 

Unfortunately I am not that well versed in bash otherwise I would volunteered :(

regards,
Seemanta


Seemanta,

caljohnsmith and any info he provides, can be trusted. He has helped me out before and has been around. Try what he recommends and work through the process(es) he directs you to do.

---

### Post by seemanta on 2009-01-08
I am not doubting caljohn or meierfra. Indeed, their efforts for ubuntu users is noteworthy. Even the stats speak for themselves: 

> Caljohn
Posts: 5,506
[B]Thanks: 40
Thanked 1,328 Times in 1,261 Posts[/B] 

But please also consider the possibility of a malicious person getting access to the comcast server where this script is hosted. Clearly there is a possibility of this happening.

You might say I am paranoid, but when you have a brand new laptop and a HDD with important stuff, paranoia pays IMHO.

That being said, I shall try to decipher the script in my free time and shall post it here if I can write a annotated version of it.


regards,
Seemanta

---

### Post by meierfra. on 2009-01-08
> 2. Reboot now using the Ubuntu live CD again(since grub won't work anyway due to step 1) and then re-install grub so that it becomes aware of the new partition device names now?

Step 2. is what is confusing me and I would proceed with the above only when I am assured that step 2 is doable.


Step 2 is doable. After you added the new partition, open a terminal in the Ubuntu LiveCD and type

```
sudo grub
```
and then at the grub> prompt:

```
find /boot/grub/stage2
```
this is just for double checking, it should return (hd0,6). Then, still at the grub prompt:

```
root (hd0,6)
setup (hd0)
quit
```

Depending on your setup and whether your UUID's have changed, you might also have to  edit fstab and menu.lst. But the above should  be enough do get the grub menu back and we can worry about the rest later.

PS.  Thanks for your concern with respect to the boot_info script. We are currently working to find a better solution than running the script from an untrusted site.

> That being said, I shall try to decipher the script in my free time and shall post it here if I can write a annotated version of it.

That would be wonderful. Let my know if you have problems deciphering, I  will  answer any question you might have.

---

### Post by seemanta on 2009-01-11
Hi meierfra,

That really helped! Many thanks to you! Actually my line of thinking that all those grub errors are due to the errors in menu.lst and /etc/fstab was wrong from day 1.

I needed to 're-install' grub. And with the steps you gave, everything was a breeze. I was then able to get the grub menu, something which was not earlier.

But even then I was not able to boot properly. Solution : I just pressed 'e' and edited the boot entries to proper device names, and I was able to get into Ubuntu. Then I made those changes permanent in menu.lst.

regards,
Seemanta

---

### Post by meierfra. on 2009-01-11
Glad you got it to work. 

PS. The script is is now hosted by a more respectable site: [https://sourceforge.net/projects/bootinfoscript/]("https://sourceforge.net/projects/bootinfoscript/")

So if you  if you  are still thinking about producing an annotated version of the script, you can submit it via  "Documentation" tab of that link.

---

### Post by teket3 on 2009-01-11
Dear everyone,
 
Our company, Beijing Teket is a specialized manufacturer of 2.4G wireless keyboard, wireless multi-media presenter and pc-based remote control.
 
Moreover, we have established business relationships with many companies around the world. We also provide OEM and ODM service, thus your designs and good ideas are welcome. Our R&D Team always develops new items, Therefore, we can better fulfill customers' specifications in a positive manner.
 
If you want to learn more about our company or products, pls visit our website:
[http://www.teket.com/en/index.htm](http://www.teket.com/en/index.htm)
 
Hopefully, we can establish good business relation on basis of mutual benefit and trust in coming future.
Looking forward to receiving your prompt reply.
 
Tks & Best regards,
 
Yolanda Tian
Beijing Teket Innovation Technology Co., Ltd.
Tel: (86)10-82894738
Fax: (86)10-82893738
E-mail/MSN/Skype: [email]teket3@teket.com[/email]
Website: [http://www.teket.com](http://www.teket.com)
Address:P.O.Box 2861, Beijing 100085, China

---

