---
title: "Dell Inspiron B120"
date: 2007-10-29
forum: Hardware &amp; Laptops
---

### Post by catch2two on 2007-10-29
I just upgraded my desktop pc and my wife's lap top to Gutsy. I was using ubuntu studio on both. Desktop works fine (except for some horrible pinkish looking screen when it first starts up that hangs around for ages. if anybody knows how to make this black, grey or anything that would be great)

Anyways, It was not easy getting my wife to switch in the first place, but she finally came around. Now i upgraded to Gutsy her wireless is not working. If i don't fix this asap i am going to be hearing about microsoft day in and day out.

I am at work at the moment so i cant remember the network manager i switched to in fesity. But basicly i used NdisWrapper in fesity then switched out the network manager for an alternate one and it all worked fine.

At the moment the new manager appears to be working, but when you click connect it gets stuck at the ip. I did enable the restricted driver and it looks like the ubuntu network manager and my one is running.

Oh, also i did get online once sinse i upgraded.

Sorry for the ramble.

Any idea?

---

### Post by henklaak on 2007-10-29
Might this help you?

[http://gentoo-wiki.com/HARDWARE_Dell_Inspiron_B120]("http://gentoo-wiki.com/HARDWARE_Dell_Inspiron_B120")

Pretty straightforward with ndiswrapper I hope...

More details here: [http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/")

Let us know how you're doing.

Regards, Henk.

---

### Post by catch2two on 2007-10-30
Okay, finally got a chance to work on this. 

I had all ready installed ndis and i was using a program called wicd to monitor my wireless networks.

Since i upgraded to Gutsy none of this works correctly. (It worked perfect in feisty)

I have uninstalled wicd and am using wi-fi radar now.

Both wicd and wifi radar show me as connected to my wireless connection, but when i open a browser i rarely can open a page. If i do get a page to open it is for a short time. If the browser is unable to open a page wicd and wifi radar still show me as conected.

Can anyone help with this problem before i lose my wife back to ms?

Thanks, 

Catch2two

---

### Post by catch2two on 2007-10-30
Strange phenomena.


I have been doing more testing and this is what i have found: 


i switched back to wicd which worked well for me in the past. 

If i click connect, it connects. Then i type a url in my browser and it goes to it.

Now if i type another one it just times out.

If i click connect again and then type that same url it goes there fine.

Any clues?

---

