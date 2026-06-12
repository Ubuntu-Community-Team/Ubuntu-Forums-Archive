---
title: "Getting my Microphone working"
date: 2008-08-12
forum: Hardware
---

### Post by chris062689 on 2008-08-12
I need help with this.
It's plugged in, I can receive audio into the Microphone, but I can't record anything.  I had it working before after I wiped the HD.
```

chris@chris-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IB (ICH9) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IB (ICH9) 2 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation Geforce 9600 GT 512mb (rev a1)
03:00.0 IDE interface: JMicron Technologies, Inc. JMB368 IDE controller
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)

```

---

### Post by eggdeng on 2008-08-12
I am using a similar audio device to yours (82801G). I got the mic working by editing the esd.conf file.
First, back up the file
```
sudo cp /etc/esound/esd.conf /etc/esound/esd.conf.old
```
Then, open it with a text editor.
```
sudo gedit /etc/esound/esd.conf
```
Replace the contents with the following.

```
[esd]
auto_spawn=1
spawn_options=-terminate -nobeeps -as 1
spawn_wait_ms=100
# default options are used in spawned and non-spawned mode
default_options=
```

Save the file and reboot the computer.

Make sure your Sound recorder / Volume Control settings are consistent. If you choose Capture as your record-from-input option, then max the volume for Capture on the recording tab of the Volume Control applet. On the options tab, choose Mic as your input source if you are using an external microphone.

---

### Post by chris062689 on 2008-08-12
> **eggdeng said:**
> I am using a similar audio device to yours 
Make sure your Sound recorder / Volume Control settings are consistent. If you choose Capture as your record-from-input option, then max the volume for Capture on the recording tab of the Volume Control applet. On the options tab, choose Mic as your input source if you are using an external microphone.

See, that's the thing, I don't know which one the microphone is plugged into: Capture, Capture 1, Front Mic, Microphone, ETC.
I'm given tons of options.

---

### Post by eggdeng on 2008-08-12
Have you edited esd.conf? Attached, a screenshot of my settings. Hope it helps.

---

### Post by chris062689 on 2008-08-12
The options I have are mind-boggling.
I just don't know which ones to choose!  :lolflag:
I've tried combinations of them, turned them all on..
Either nothing comes out, or it's static.

---

### Post by Slug71 on 2008-08-12
> **eggdeng said:**
> I am using a similar audio device to yours (82801G). I got the mic working by editing the esd.conf file.
First, back up the file
```
sudo cp /etc/esound/esd.conf /etc/esound/esd.conf.old
```
Then, open it with a text editor.
```
sudo gedit /etc/esound/esd.conf
```
Replace the contents with the following.

```
[esd]
auto_spawn=1
spawn_options=-terminate -nobeeps -as 1
spawn_wait_ms=100
# default options are used in spawned and non-spawned mode
default_options=
```

Save the file and reboot the computer.

Make sure your Sound recorder / Volume Control settings are consistent. If you choose Capture as your record-from-input option, then max the volume for Capture on the recording tab of the Volume Control applet. On the options tab, choose Mic as your input source if you are using an external microphone.

Would that work for internal mic too?

---

### Post by eggdeng on 2008-08-13
@chris062689 Check Microphone on the Select tracks to be visible dialog. Then you will be able to control it from the recording tab of the volume control applet.
@Slug71 In my case, yes but quality is really poor.

---

### Post by Shortyz50Rock on 2008-08-13
HOW TO MAKE QUICK MONEY WITH ONLY $6.00?!!! turn 6 dollars into thousands, 
IT REALLY WORKS!!!!!

AMAZING PLAN TO BECOME RICH IN DAYS AMAZING PLAN TO BECOME RICH!! HOW
TO BECOME RICH HOW TO TURN SIX DOLLARS INTO THOUSANDS OF DOLLARS:
READING THIS COULD CHANGE YOUR LIFE! IT DOES WORK! A little while back,
I was browsing through newsgroups, just like you are now, and came
across an article similar to this that said you could make thousands of
dollars within weeks with only an initial investment of $6.00! So I
thought," Yeah, right, this must be a scam", but like most of us, I was
curious, so I kept reading. Anyway, it said that you send $1.00 to each
of the 6 names and address stated in the article. You then place your
own name and address in the bottom of the list at #6, and post the
article in at least 200 newsgroups. (There are thousands) No catch,
that was it. So after thinking it over, and talking to a few people
first, I thought about trying it. I figured what have I got to lose
except 6 stamps and $6.00, right? Like most of us I was a little
skeptical and a little worried about the legal aspects of it all. So I
checked it out with the U.S. Post Office (1-800-725-2161) and they
confirmed that it is indeed legal! Then I invested the measly $6.00.
Well GUESS WHAT!!.. within 7 days, I started getting $$$$$ in the
mail! I was shocked! I figured it would end soon, but the CASH just
kept coming in. In my first week, I made about $25.00. By the end of
the second week I had made a total of over $1,000.00! In the third week
I had over $10,000.00 and it's still growing. This is now my fourth
week and I have made a total of just over $42,000.00 and it's still
coming in rapidly. It's certainly worth $6.00, and 6 stamps. Let me
tell you how this works and most importantly, why it works..also,
make sure you print a copy of this article NOW, so you can get the
information off of it as you need it.
STEP 1: Get 6 separate pieces of paper and write the following on each
piece of paper "PLEASE PUT ME ON YOUR MAILING LIST" along with your
name and address. Now get 6 US $1.00 bills and place ONE inside EACH of
the 6 pieces of paper so the bill will not be seen through the envelope
to prevent thievery. Next, place one paper(with a $1.00 bill inside) in
each of the 6 envelopes and seal them. You should now have 6 sealed
envelopes, each with a piece of paper stating the above phrase, your
name and address, and a $1.00 bill. What you are doing is creating a
service by this.
THIS IS ABSOLUTELY LEGAL! Mail the 6 envelopes to the following
addresses:



1. Justin Jones, 121 marlborough road, w. hempstead,Ny. 11552, USA
2. Regan Hines, 22 Stature Drive, Newark, DE, 19713, USA
3. Catherine Mendoza, 2017-565 Sherbourne St., Toronto, ON, Canada M4X
1W7
4. Eric Thack, 425 Deckinson St., Philadelphia, PA, 19147, USA
5. Joseph Scribbick, 113 North 4th Street, Minersville, PA, 17954, USA
6. Brandi Pucci, 34 Cherry Street, Cressona, PA, 17954, USA

STEP 2: Now take the #1 name off the list that you see above, move the
other names up (6 becomes 5, 5 becomes 4, etc..) and add YOUR Name as
number 6 on the list. STEP 3: Change anything you need to, but try to
keep this article as close to original as possible. Now, post your
amended article to at least 200 newsgroups. (I think there are close to
24,000 groups) All you need is 200, but remember, the more you post,
the more CASH you make!
DIRECTIONS ---HOW TO POST TO NEWSGROUPS
Step 1) You do not need to re-type this entire letter to do your own
posting. Simply put your cursor at the beginning of this letter and
drag your cursor to the bottom of this document, and select 'copy' from
the edit menu. This will copy the entire letter into the computers
memory.
Step 2) Open a blank "notepad" file under accessories in windows and
place your cursor at the top of the blank page. From the 'edit' menu
select 'paste'. This will paste a copy of the letter into notepad so
that you can add your name to the list.
Step 3) Save your new notepad file as a .txt file. If you want to do
your postings in different sittings, you'll always have this file to go
back to.
Step 4) Use Netscape or Internet explorer and try searching for various
newsgroups (on-line forums, message boards, chat sites, bulletin boards
discussions.) .
Step 5) Visit these message boards and post this article as a new
message by highlighting the text of this letter and selecting paste
from the edit menu. Fill in the Subject, this will be the header that
everyone sees as they scroll through the list of postings in a
particular group, click the post message button.
You're done with your first one! Congratulations. THAT’S IT! All you
have to do is jump to different newsgroups and post away, after you get
the hang of it, it will take about 30 seconds for each newsgroup!
**REMEMBER, THE MORE NEWSGROUPS YOU POST IN, THE MORE CASH YOU WILL
MAKE!! BUT YOU HAVE TO POST A MINIMUM OF 200** That's it!
You will begin receiving $$$$ from around the world within days!
You may eventually want to rent a P.O. Box due to the large amount of
mail you will receive. If you wish to stay anonymous, you can invent a
name to use, as long as the postman will deliver it. **JUST MAKE SURE
ALL THE ADDRESSES ARE CORRECT.**
Now the WHY part:
Out of 200 postings, say I receive only 5 replies (a very low example).
So then I made $5.00 with my name at #6 on the letter. Now, each of the
5 persons who just sent me $1.00 make the MINIMUM 200 postings, each
with my name at #5 and only 5 persons respond to each of the original
5, that is another $25.00 for me, now those 25 each make 200 MINIMUM
posts with my name at #4 and only 5 replies each, I will bring in an
additional $125.00! Now, those 125 persons turn around and post the
MINIMUM 200 with my name at #3 and only receive 5 replies each, I will
make an additional $626.00! OK, now here is the fun part, each of those
625 persons post a MINIMUM 200 letters with my name at #2 and they each
only receive 5 replies, that just made me $3,125.00!!! Those 3,125
persons will all deliver this message to 200 newsgroups with my name at
#1 and if still 5 persons per 200 newsgroups react I will receive
$15,625,00! With a original investment of only $6.00! AMAZING! When
your name is no longer on the list, you just take the latest posting in
the newsgroups, and send out another $6.00 to names on the list,
putting your name at number 6 again, and start posting again. The thing
to remember is, do you realize that thousands of people all over the
world are joining the internet and reading these articles everyday,
JUST LIKE YOU are now!! So can you afford $6.00 and see if it really
works?? I think so.. People have said, "what if the plan is played out
and no one sends you the money? So what! What are the chances of that
happening when there are tons of new honest users and new honest people
who are joining the internet and newsgroups everyday and are willing to
give it a try? Estimates are at 20,000 to 50,000 new users, everyday,
with thousands of those joining the actual internet. Remember, play
FAIRLY and HONESTLY and this will work. You just have to be honest.
Make sure you print this article out RIGHT NOW, also. Try to keep a
list of everyone that sends you money and always keep an eye on the
newsgroups to make sure ever.

---

### Post by chris062689 on 2008-08-13
....

---

