---
title: "network scanner IP change"
date: 2012-11-27
forum: Hardware
---

### Post by lincoln32 on 2012-11-27
I have a Brother MFC-9440CN and was working fine till I changed the IP range
I am unable to change the Scanner to a new Ip address 

$ brsaneconfig3 -q | grep SCANNER
  0 SCANNER             "MFC-9440CN"         I:192.168.5.3

I need to change it to 192.168.1.09
this is what I used to set it up the first time-I did try again with new IP
$ brsaneconfig3 -a name=SCANNER model=MFC_9440CN ip=192.168.5.3
I also tried to remove it with but no luck not sure what name to use
brsaneconfig3  -r  SCANNER-NAME

support info
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn2.html#2](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn2.html#2)

what did I do wrong it may well be my minimal bash knowlage:confused:

---

### Post by staifan13 on 2013-10-21
[SIZE=2]hey I know this post is one year hold [/SIZE]but it help me with the same problem .
the command is : 
[COLOR=#000000][FONT=Arial]**brsaneconfig3 -r SCANNER-NAME[SIZE=2] where scanner -name here is SCANNER because you set this then you type[/SIZE] **[/FONT][/COLOR][COLOR=#000000]$ brsaneconfig3 -a name=_SCANNER_ model=MFC_9440CN ip=192.168.5.3 therefore you have to type : brsaneconfig3 -r SCANNER first ...
[/COLOR][COLOR=#000000][FONT=Arial][B]Stéphan
[/B][/FONT][/COLOR]

---

