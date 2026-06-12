---
title: "asus EeePC troubles already."
date: 2008-12-01
forum: Hardware
---

### Post by cmay on 2008-12-01
hi.
i just got a asus Eeepc that has xandros linux in it. i really do not like xandros at all for many reasons. having the usb drive letters come up as c:\ is not my idea of getting linux . anyway i donwloaded a pair of different alternatives and i tried to use the usb creator in intrepid ibex. which actually works with some of the iso images. i have then anohter usb stick with belenix (solaris on a usb stick) that i tried also. the worst thing to discover was that the cd i bourght with eeebuntu cant figure out to set the keyboard to danish at all. 

i would say that besides the point of having a asus Eee pc to go with me when i go to the hospital its a really amusing  little machine that i could have a lot of fun playing with to find out as much as possible about how to make as many distros run on it on usb sticks or installed but the fact is that i as stated need a system that just works when i am in the hospital and i got this exact model as it was the most cheap one and i cant afford anohter model laptop.  its the asus EeePC 701sd model and i would like to hear what you can adwise me to do concerning this alternative to xandros. which i simply do not want out of the user unfreindly way it works. 
i mean i cant have usb sticks show up as c:\ or d:\ and then it has a lot of click ok message dialogs also. i found that its even hard to compile a program and use the standard gcc compiler since its changed some libraries which is not very cool when i am a (soon to be) hobby programmer when i am feeling up to it. so all the good things in linux is gone in xandros and i want ubuntu or solaris or even bsd on it. as long as i can use the default keyboard outlay and i can make it work and be stable. which by the way xandros is not after updating it i been told. 

can you guys offer me some advise and please provide links also . 
i would also say the first i plan to do is get up in the morning and call  asus danish department if there is such and tell them that they really need to listen to customers that wants linux and give them ubunutu preinstalled on these machines. 

sorry if it sounds like i am bashing xandros but i am really trying not to. its just that my main interest is unix and linux and this specific distro simply remind me too much of windows than linux. i need to have it like debian or ubuntu  or bsd or solaris if i am trying to write some things while i am in the hospital. ohter than that i cant complaint over the product as such. i am just a user with some specific needs and i like the machine also its not that.  

i hope i did not offend any one. i am also trying to find a way to get this to work wiht ubuntu as good as possible as there is really many people here buyin these machines so if i could make it as painless as possible for these new users to maybe try ubuntu or maybe anohter linux then i would be very happy. 

thanks for reading this and thanks for your time.

---

### Post by snowpine on 2008-12-01
Hi there, I have never actually used Xandros (my eee came with XP preinstalled) but I have heard a lot of bad things. Please do not judge all Linux distros based on the custom eee Xandros. :)

My eee is a different model than yours (900ha) so I am not 100% sure my experience will match yours. In my opinion, the easiest eee distro is Ubuntu eee 8.04.1 ([http://ubuntu-eee.com](http://ubuntu-eee.com)). There is a customized Unetbootin utility on their website that copies Ubuntu eee to a USB stick or SD card similar to a Live CD. You can run from the USB/SD in Live mode, or install to your internal drive. I recommend installiing to the internal drive for best performance. However, I do not particularly love the Ubuntu eee interface, so I've moved on to other options.

The next most easy option is to use the custom kernel from array.org. This is the same kernel used in Ubuntu eee, available separately. The advantage to this method is you can take any Ubuntu 8.04 or 8.10 variation (Xubuntu, Kubuntu, etc.) and make it work on the eee. I hear a lot of 700  users prefer Xubuntu since it is a bit smaller. 

Personally, my favorite eee distro so far (I experiment a lot!) is CrunchBang. I am typing this using CrunchBang 8.10 with the array.org kernel. It takes about 2gb for a full install, so it will fit nicely on your 4gb SSD. CrunchBang is an international distro, so I bet you can localize it for your Danish keyboard/language. (I am in the USA.) 

Other distros I have tried and liked include Debian Lenny (with the special installer: [http://wiki.debian.org/DebianEeePC/HowTo/Install](http://wiki.debian.org/DebianEeePC/HowTo/Install)) and Sidux. 

Regarding Asus' choice to pre-install Xandros on the eee, understand that it is a major international business deal involving millions of units shipped. These decisions usually come down to money. ;) Dell is the only major manufacturer I'm aware of that ships Ubuntu.

Don't give up! :)

---

### Post by cmay on 2008-12-01
> My eee is a different model than yours (900ha) so I am not 100% sure my experience will match yours. In my opinion, the easiest eee distro is Ubuntu eee 8.04.1 ([http://ubuntu-eee.com]("http://ubuntu-eee.com/")). There is a customized Unetbootin utility on their website that copies Ubuntu eee to a USB stick or SD card similar to a Live CD. You can run from the USB/SD in Live mode, or install to your internal drive. I recommend installiing to the internal drive for best performance. However, I do not particularly love the Ubuntu eee interface, so I've moved on to other options.this is the one i tried . i do not understand how come it cant set a danish working keyboard layout.  ubuntu seems to be more supported on almost anything so this is a big surprise. 

i have been using debian since sarge and ubuntu since dapper so i would really not like it to have xandros on this little machine. i need a working keyboard and a debian based distro that simply looks like linux and acts like linux like i am used to. 

this crunch bang linux works straigth out of the box or does you need to do a lot of manual configuring to make it work. ?  i think i want rather debian if i need to configure a lot of things anyway. 

thanks.

---

### Post by snowpine on 2008-12-01
> **cmay said:**
> this is the one i tried . i do not understand how come it cant set a danish working keyboard layout.  ubuntu seems to be more supported on almost anything so this is a big surprise. 

i have been using debian since sarge and ubuntu since dapper so i would really not like it to have xandros on this little machine. i need a working keyboard and a debian based distro that simply looks like linux and acts like linux like i am used to. 

this crunch bang linux works straigth out of the box or does you need to do a lot of manual configuring to make it work. ?  i think i want rather debian if i need to configure a lot of things anyway. 

thanks.

I am really sorry I can't give you help with your Danish keyboard. I live in the US so most distros support my keyboard easily. :(

Regarding CrunchBang, it is basically Ubuntu + Openbox windows manager + a nice minimalist dark theme. It has the same support for the eee as regular Ubuntu, which is to say, you need to install the array.org kernel to get wireless working. Here is a tutorial I wrote: [http://crunchbanglinux.org/forums/topic/11/crunchbang-on-the-eee-pc/](http://crunchbanglinux.org/forums/topic/11/crunchbang-on-the-eee-pc/)

If you are not already familiar with the site, please check out [http://forums.eeeuser.com](http://forums.eeeuser.com) . It is a great community with a lot of international eee users. :)

---

### Post by cmay on 2008-12-01
yeah it look kinda cool. i buy a lot of stuff at a online linux shop which i have found some links for regarding the matter of users wanting to get something else installed than xandros so i hope that i can find as much as possible since i do really think that the ones that learn xandros linux does not really learn linux.
 i want to find out as much as i can fast since its a popular laptop.
 
my lack of will towards xandros is that i cant even begin understand why a linux distro would call the folders like they are in windows and show drive letters like they are in windows. and make it so hard to actually install programs and even update it sometimes. 

i am going to try this crunch bang linux out and see how the keyboard layout turns out. 
thanks a lot :)

---

### Post by supchaka on 2008-12-01
If I might just throw this out there, did you enable the advanced desktop of Xandros at all? Its really not too bad. If you're using what they call the "easy mode" then I can understand why you would want to get rid of it. You can google it, enabling advanced desktop xandros for the guide.

---

### Post by cmay on 2008-12-02
i found that after searching a while.  i am a gnome user and debian user so i cant relate to this. also this way of renaming the dev/sda into e:\ i cant understand. but i found out i can plug in a extern usb keyboard and run a distro like open-solaris on a usb stick. so i i am guessing i can just use the system on the flash drive as a backup for simple things that i need when i get to the hospital and then get a extern usb hardrive i can have ubuntu on and use the extern screen and plug in mouse land keyboard like a normal stationary . 
until i find a distro that just fits the bill .  but its not all bad i just do not like xandros. for many reasons. i use linux out of many  reasons one is i firmly believe in the open-source and i do not like when a linux distro starts to hold back on sources for drivers like xandros does. its a kinda political thing ;)

---

### Post by gonzomalan on 2008-12-03
> **cmay said:**
> this is the one i tried . i do not understand how come it cant set a danish working keyboard layout.  ubuntu seems to be more supported on almost anything so this is a big surprise.

To be fair, Ubuntu-eee is not developed by Canonical, the company behind Ubuntu. Canonical released an official netbook version of Ubuntu, and call it "Ubuntu Netbook Remix". If you want to try it out, here's a link: [http://www.canonical.com/projects/ubuntu/nbr](http://www.canonical.com/projects/ubuntu/nbr)

---

### Post by cmay on 2008-12-03
thanks :D

---

### Post by lorenfb on 2008-12-05
You might consider this as a solution:

[http://cgi.ebay.com/Ubuntu-8-04-1-Installed-8GB-SD-Card-Asus-Eee-PC-701-900_W0QQitemZ270310668693QQcmdZViewItemQQptZUS_Software?hash=item270310668693&_trksid=p3286.c0.m14&_trkparms=72%3A1205%7C66%3A2%7C65%3A12%7C39%3A1%7C240%3A1318%7C301%3A1%7C293%3A1%7C294%3A50](http://cgi.ebay.com/Ubuntu-8-04-1-Installed-8GB-SD-Card-Asus-Eee-PC-701-900_W0QQitemZ270310668693QQcmdZViewItemQQptZUS_Software?hash=item270310668693&_trksid=p3286.c0.m14&_trkparms=72%3A1205%7C66%3A2%7C65%3A12%7C39%3A1%7C240%3A1318%7C301%3A1%7C293%3A1%7C294%3A50)

Although many might not like paying for a Ubuntu distro when 
most all are free, some do value time to tweak an install
versus spending for a "clean" install, i.e. $25/$50 versus
maybe hours of effort.

---

### Post by gonzomalan on 2008-12-06
> **cmay said:**
> thanks :D

you're welcome :)

---

