---
title: "Virus attack"
date: 2008-10-09
forum: General Help
---

### Post by tajs on 2008-10-09
I know, I know, believe me I know Ubuntu does not suffer from virus attacks.....However.

Three days ago I was browsing the net when a pop up appeared saying my machine needed scanning for viruses (ANTIVIRUS 2009 may their bums be infested with the fleas of a thousand camels) and before I could say bugger the program started. I shut my machine down with the power button as nothing else responded.

When I restarted my machine all was well until I tried to shut down. It took my PC 4+ minutes to close down during which time the PC was totally unresponsive.

Then the following day a contact in the USA emailed me saying according to his copy of Norton anti Virus my emails were infected with W32.Netsky.P@mm!enc .

My PC still takes 4+ mins to shut down.....can anyone offer advice???

:confused:

---

### Post by Calmatory on 2008-10-09
So you assume that the popup got you a virus and now it infects your email? In which website did you get this popup? Was it in some email perhaps? If not, then it sounds odd due to the reason that usually the viruses which infect themselves to emails also spread via emails.

Could it be a false positive from your contact's side?

Edit: It seems that W32.Netsky.P@mm!enc indeed affects almost all OS'es, Windows, DOS, Unix, Linux and mac. Those at least.

---

### Post by AlexBellisBrown on 2008-10-09
Its hard to belive that i virus is the cause of the problem, but if you wish, you can install a antivirus program from inside the Add/Remove programs, Give it a spin and let us know.

---

### Post by Calmatory on 2008-10-09
> **AlexBellisBrown said:**
> Its hard to belive that i virus is the cause of the problem, but if you wish, you can install a antivirus program from inside the Add/Remove programs, Give it a spin and let us know.

Well, at least not because "linux is secure", since that virus indeed can infect linux machines. If it can run on user privileges and cause harm, then OP is not safe. :|

---

### Post by iKonaK on 2008-10-09
:lolflag:   try [noscript]("https://addons.mozilla.org/en-US/firefox/addon/722") if you can't surf the net, or delete your /home directoy to reset all....my god, virus in GNU/Linux....

---

### Post by StooJ on 2008-10-09
Hang on, just to check something:

What OS were you using at the time?

I suspect the OP mentioned the lack of virii in Ubuntu to head off any responses along the lines of "Well, you should have been using linux" :)

> **Calmatory said:**
> 
Edit: It seems that W32.Netsky.P@mm!enc indeed affects almost all OS'es, Windows, DOS, Unix, Linux and mac. Those at least.

Where did you find that, Calmatory? I don't think that can be correct, since W32.Netsky.P@mm! works partly by exploiting a vulnerability in older versions of Internet Explorer.

---

### Post by Tomatz on 2008-10-09
> **tajs said:**
> I know, I know, believe me I know Ubuntu does not suffer from virus attacks.....However.

Three days ago I was browsing the net when a pop up appeared saying my machine needed scanning for viruses (ANTIVIRUS 2009 may their bums be infested with the fleas of a thousand camels) and before I could say bugger the program started. I shut my machine down with the power button as nothing else responded.

When I restarted my machine all was well until I tried to shut down. It took my PC 4+ minutes to close down during which time the PC was totally unresponsive.

Then the following day a contact in the USA emailed me saying according to his copy of Norton anti Virus my emails were infected with W32.Netsky.P@mm!enc .

My PC still takes 4+ mins to shut down.....can anyone offer advice???

:confused:


Reported! 

Troll

1 post??? Do you think we are stupid???

---

### Post by tajs on 2008-10-09
Hi

I simply do not know enough to assume anything.

I do not remember the site I was in when it happened..no it was not a naughty site:-)

I am pretty sure it did not come via email as I have has trouble with this AntiVirus software on my wifes Xp based PC. It is very pervasive and bloody hard to get rid of.
and she got attacked as I did, by visiting a web site. I ended up having to do a full reinstall.

I do not understand what you mean by false positive?

---

### Post by tajs on 2008-10-09
Will do thanks.

---

### Post by tajs on 2008-10-09
I found noscript yesterday and it is now installed. However I want to sort out the shut down issue. But thanks for responding.

---

### Post by tajs on 2008-10-09
Hi Tomatz

I do not understand your reply.

Reported!

1 Post??? Do I think you are stupid!

---

### Post by airtonix on 2008-10-09
info on the worm here : [http://www.symantec.com/security_response/writeup.jsp?docid=2004-032110-4938-99&tabid=2](http://www.symantec.com/security_response/writeup.jsp?docid=2004-032110-4938-99&tabid=2)


> **tajs said:**
> 
I do not remember the site I was in when it happened..no it was not a naughty site:-)

We asked what operating system you were using too.

> **tajs said:**
> 
I am pretty sure it did not come via email as I have has trouble with this AntiVirus software on my wifes Xp based PC. 


Ok stop right here...let me get this right : 
1 - your pretty sure it didnt come via email even though its a email based worm.
2 - you base this assumption on the fact that your wifes antivirus program is giving you problems?
3 - to top it all off its a piece of software giving you problems...on a windows machine.
But im not sure how your able to say it didnt come from an email, based on the fact that your wife's antivirus is giving you "problems"
> **tajs said:**
> 
It is very pervasive and bloody hard to get rid of.


Now what are you talking about here ? what is pervasive and hard to get rid of (choose one) : 
1 - windows in general?
2 - the anti-virus software?
3 - your wife?
4 - the internet ?
5 - the computer your wife is using?
6 - ???
7 - the virus?
> **tajs said:**
> she got attacked as I did, by visiting a web site.
so was her computer infected before you decided to assume that ubuntu is also infected? (considering that this virus requires win32 enviroment to execute in.)
> **tajs said:**
>  I ended up having to do a full reinstall.

nothing abnormal there about windows

> **tajs said:**
> 
I do not understand what you mean by false positive?

[http://en.wikipedia.org/wiki/Type_I_and_type_II_errors](http://en.wikipedia.org/wiki/Type_I_and_type_II_errors)
[http://en.wikipedia.org/wiki/False_positive_paradox](http://en.wikipedia.org/wiki/False_positive_paradox)

I think that in your haste to isolate the so-called virus with a panic attack on the power button did more damage.

have you at least done a fsck? checked any logs? /var/log/auth.log will contain any sudo access, which is required on ubuntu to gain root.

To eve begin working out what is causing the slow down in boot up and shutdowns(it is taking 4mins to shutdown and bootup isnt it? or only one of them?)
i would start looking at logs galore!

```
dmesg | tail
```

And considering that page i linked first, i would start looking for the files that the virus is supposed to create. if they exist then you might actually have something....but only on a slim chance. 

reason i think you have no virus : The worm attempts to exploit the issue described as Microsoft IE MIME Header Attachment Execution Vulnerability (BID 2524), to execute the attachment as soon as the email is viewed.

---

### Post by Tomatz on 2008-10-09
I'm not going to get into an argument here but i think you are talking tosh. The virus you mention ONLY infects windows 9x and NT systems (see below).

[http://www.symantec.com/security_response/writeup.jsp?docid=2004-050511-4636-99](http://www.symantec.com/security_response/writeup.jsp?docid=2004-050511-4636-99)

Hopefully the moderators will remove this useless and time consuming thread.

---

### Post by Calmatory on 2008-10-09
> **StooJ said:**
> 

Where did you find that, Calmatory? I don't think that can be correct, since W32.Netsky.P@mm! works partly by exploiting a vulnerability in older versions of Internet Explorer.

Right. Once again I got tricked by googling. Shoudl've paid more attention. ;)

> **Tomatz said:**
> I'm not going to get into an argument here but i think you are talking tosh. The virus you mention ONLY infects windows 9x and NT systems (see below).

[http://www.symantec.com/security_response/writeup.jsp?docid=2004-050511-4636-99](http://www.symantec.com/security_response/writeup.jsp?docid=2004-050511-4636-99)

Hopefully the moderators will remove this useless and time consuming thread.

His contact is saying that the email was infected. However, this does not mean that his machine is infected. Besides, the email could be sent from anywhere, even from infected Windows machine. Thus frankly I find your accusing him of trolling a bit harsh.

---

### Post by Interpreter on 2008-10-09
The ****,
got my attention for a sec there ))

My guess is that its not even a hoax, he just realy aint PC literate and freaked out over some "Russian fake Norton add popup" which just happend to FLASH-crash his machine and his wife had a real XP virus at the same time ...

Funny scenario though, kept me entertained.

---

### Post by hyper_ch on 2008-10-09
one more fake linux virus warning...

---

### Post by Calmatory on 2008-10-09
> **hyper_ch said:**
> one more fake linux virus warning...
...and what does this mean?

---

### Post by AlexBellisBrown on 2008-10-09
This isnt right... there must be some other problem here. I dont belive this virus is capable of penetrating Linux. Its a W32 virus! Written for Windows!!! Maybe if you run it with Wine?;)

The pop up sounds like one of them stupid ones with use flash animations to make you think its scanning your machine... Utter rubbish... meh.

---

### Post by Interpreter on 2008-10-09
> **AlexBellisBrown said:**
> This isnt right... there must be some other problem here. I dont belive this virus is capable of penetrating Linux. Its a W32 virus! Written for Windows!!! Maybe if you run it with Wine?;)

The pop up sounds like one of them stupid ones with use flash animations to make you think its scanning your machine... Utter rubbish... meh.
Dito

More details please, no offense but to see whether you overreacted to that "coincidence" or whether there is a bit more to it, you might come up with tech savy facts.

Right now all we have is your "theory", which - at least to me- sounds "unintentionally funny" to be honest.

---

### Post by Sef on 2008-10-09
Do you run an email client, like Thunderbird or Evolution?   If so, then viruses could run on top of Linux, and you could infect your friends who have Windows computers.

---

### Post by lisati on 2008-10-09
I've seen those popups too. My advice is: PAY ATTENTION. 
[LIST=1]
[*]When using *ubuntu, you'd expect the theme of a "window" to match your *ubuntu them, NOT some MS Windows theme
[*]Watch the pointer as you move your mouse around the screen - many popups of this kind are a big image file, and the pointer will remain the same regardless of whether it's over a "button" or not
[*]Be cautious of email from people you don't know
[/LIST]

---

### Post by AlexBellisBrown on 2008-10-09
> **Sef said:**
> If so, then viruses could run on top of Linux

But not one that is written for Windows, surely? Its a totally different programing language... the virus would just sit there in its archive, not doing anything.

---

### Post by lisati on 2008-10-09
> **AlexBellisBrown said:**
> But not one that is written for Windows, surely? Its a totally different programing language... the virus would just sit there in its archive, not doing anything.

It would take a lot of ingenuity to come up with an executable binary that would work with both *nix and Windows. 

It is possible in some circumstances to wrap up an MS-DOS program and a Windows program inside the same .EXE file but I suspect  that the same technique wouldn't work too well for Windows & Linux....

---

### Post by Sef on 2008-10-09
> But not one that is written for Windows, surely? Its a totally different programing language... the virus would just sit there in its archive, not doing anything.

The virus won't harm the Linux box; however, it can be sent out with an email, if the Linux user uses an email client.

---

### Post by Calmatory on 2008-10-09
It doesn't necessarily need to be an executable/binary. For example plug-ins/extensions and/or scripts could cause some harm. And they are platform independent.

---

### Post by lisati on 2008-10-09
> **Calmatory said:**
> It doesn't necessarily need to be an executable/binary. For example plug-ins/extensions and/or scripts could cause some harm. And they are platform independent.

Good point...and MS Word document macros? But then again, how much harm could be done without the user having to give a password for root privileges?

---

### Post by Calmatory on 2008-10-09
> **lisati said:**
> Good point...and MS Word document macros? But then again, how much harm could be done without the user having to give a password for root privileges?Nowadays the viruses/malware does not necessarily try to do harm for the user, they just sniff data. I doubt it needs much permissions to be able to copy the email and redirect the copy to a proxy email and via it to the own address. This way the creator of the malware can sniff info from the victim and does not need privileges. The best part being that the user does not even know that he/she has such a malicious piece of code running as the malware does not make itself visible by any way.

---

### Post by Kevbert on 2008-10-09
If the original poster is using anything to emulate windows, the windows part and any shared folders with windows might be infected, BUT it should not cause any problems with linux.  The only way I would have thought he could pass on the virus is via attachments or by forwarding messages.  
I've had very old windows viruses on my PC when using DosBox but ClamAv found them.  Had no problems ever (touches wood) with Linux or Ubuntu and viruses, malware, adware, spyware.  After all it isn't Windows!!!
That's my two cents.

---

### Post by Bucky Ball on 2008-10-09
> **tajs said:**
> 
I am pretty sure it did not come via email as I have has trouble with this AntiVirus software on my wifes Xp based PC. It is very pervasive and bloody hard to get rid of.
and she got attacked as I did, by visiting a web site. I ended up having to do a full reinstall.

I do not understand what you mean by false positive?

If you are both on the same LAN, it will get in regardless. :)

Best doctor the router if poss.

---

### Post by AlexBellisBrown on 2008-10-09
Just a quick question, surely, if a virus was to propogate using thunderbird, or evolution, would it show up in "attachments" once it was sent?

---

### Post by Terry S on 2008-10-09
> **AlexBellisBrown said:**
> Its hard to belive that i virus is the cause of the problem, but if you wish, you can install a antivirus program from inside the Add/Remove programs, Give it a spin and let us know.

Hi

I installed the Virus scanner from add/remove and ran it. It did not report anything. Hey Ho. Thanks for the advice.

---

### Post by CEB2nd on 2008-10-09
It might be a good idea to install [avast antivirus]("http://www.avast.com/eng/download-avast-for-linux-edition.html") to get a second opinion.

---

### Post by Terry S on 2008-10-09
> **tajs said:**
> I know, I know, believe me I know Ubuntu does not suffer from virus attacks.....However.

Three days ago I was browsing the net when a pop up appeared saying my machine needed scanning for viruses (ANTIVIRUS 2009 may their bums be infested with the fleas of a thousand camels) and before I could say bugger the program started. I shut my machine down with the power button as nothing else responded.

When I restarted my machine all was well until I tried to shut down. It took my PC 4+ minutes to close down during which time the PC was totally unresponsive.

Then the following day a contact in the USA emailed me saying according to his copy of Norton anti Virus my emails were infected with W32.Netsky.P@mm!enc .

My PC still takes 4+ mins to shut down.....can anyone offer advice???

:confused:



To all who replied to my original post.

At NO TIME did I say I HAD a Virus.
I specifically stated Ubuntu could not be affected by virus software.
I then went on to relate a set of events and asked for advice.
Yes, I am a very new and inexperienced user of Ubuntu.

I run Ubuntu hardy 64.

I use Thunderbird

I do not run windows of any flavour on my PC.

My wife did not have trouble with her installed virus checker.

If you would like to take the trouble to look up AntiVirus 2009 it is regarded as a highly undesirable piece of software //www.removal-instructions.com/removeAntivirus2009.html 
:shock:
The response to my previous requests for assistance have been outstanding. Not so this time.

I would like to thank all who tried to help and to the others...If you feel you want to reply to a post please read the post carefully before insulting the poster.

---

### Post by Interpreter on 2008-10-09
Well I'm by all means a pacifistic person but for that post there I feel the urgent need to !$%?& you.
Wow Id love to insult you here but I fear the mods will end up banning me for that.
What a friggin con man you are. 
If your initial post wasnt supposed to sound like you'd fear that you'd been ATTACKED BY A VIRUS then I dunno what Im reading wrong.

(I mean common look at the thread name for christ's sake)

I'll leave this thread at once, cuz arguing would result in me calling you animal names.

Apologies if you feel even more attacked now but I am now left with the impression that you're "some kiddo bored at school provoking random folks on help boards".

Bye.

---

### Post by Kevbert on 2008-10-09
Terry S. It may be worth you installing Adblock Plus and NoScript add-ons if you're using Firefox (to minimize ads, control javascript etc). As one of the administrators points out here, if you get an email from an unknown source don't even open it. Just delete it and make sure it's purge from the system. Safety first.
I'm also from a Windows background and was surprised by the lack of need for security programs in Linux in general.  The best thing to do is to be on the safe side.  I use clamav/tk and ufw, but have yet to get the firewall broken into.  Yes I've had windows viruses but clamav seems to be sufficient.  The worst problem could potentially be rootkits, but you have to download them (from an untrusted source) and for that you can use rkhunter (plus another).
Linux is only as secure as you want it to be, default is very secure.

---

### Post by jerome1232 on 2008-10-09
> **Terry S said:**
> To all who replied to my original post.

At NO TIME did I say I HAD a Virus.
I specifically stated Ubuntu could not be affected by virus software.
I then went on to relate a set of events and asked for advice.
Yes, I am a very new and inexperienced user of Ubuntu.

I run Ubuntu hardy 64.

I use Thunderbird

I do not run windows of any flavour on my PC.

My wife did not have trouble with her installed virus checker.

If you would like to take the trouble to look up AntiVirus 2009 it is regarded as a highly undesirable piece of software //www.removal-instructions.com/removeAntivirus2009.html 
:shock:
The response to my previous requests for assistance have been outstanding. Not so this time.

I would like to thank all who tried to help and to the others...If you feel you want to reply to a post please read the post carefully before insulting the poster.


You know it's against forum rules to have two accounts right?

---

### Post by Sub101 on 2008-10-09
Firstly IF the OP has two accounts the Forum Staff will know as they log IP's.

Secondly im amazed at the response this post has received. Being treated with such hostility. Admins have posted in this thread which surely is enough of a blessing for others.

To the OP. I would suggest the comment Sef made would be most likely and that has coursed the message you sent to another to appear to have a virus. Or you have forwared a message/attachment which did have a virus. 

And the issue regarding taking a long time to shut down. I had the same issue recently but on the next update it resolved itself. I did not do anything to fix it it just did. So maybe wait till new updates and see if that resolves it.

---

### Post by hyper_ch on 2008-10-09
> **Sub101 said:**
> Firstly IF the OP has two accounts the Forum Staff will know as they log IP's.
Maybe they will know...  maybe you need to point them to it... one IP, two nicks doesn't mean much - think of corporations/universities that have one public IP...

> **Sub101 said:**
> Secondly im amazed at the response this post has received. Being treated with such hostility.
I'm amazed at the flaming title and wording has been used by the OP and try to mislead people here on the forums...

---

### Post by Sub101 on 2008-10-09
As far as im aware the admins are very good at picking up on it. I know of a case were a brother was mistakenly banned when his sibling was on the same network. 

And the flaming title? I do not consider 'virus attack' to be a flame. How can it be? It isn't 'Ubuntu security is rubbish as I got a virus'. The first line of the post even states he is aware that Linux can not get viruses (however I believe they have been written just not in the wild). Perhaps the title was a poor choice, never the less the content of the post appears to be a genuine request for help.

---

### Post by Terry S on 2008-10-09
> **jerome1232 said:**
> You know it's against forum rules to have two accounts right?

I do not have two accounts.

---

### Post by jerome1232 on 2008-10-09
> **Terry S said:**
> I do not have two accounts.

You posted from Terry S, quoting a post by tajs, saying it was your post. Perhaps I misunderstood and you weren't saying the post by tajs was your original post.

---

### Post by scouser73 on 2008-10-09
Just thought I'd throw my two pence worth in, according to Symantec, that virus W32.Netsky.P@mm!enc only affects Windows. [http://www.symantec.com/security_response/writeup.jsp?docid=2004-050511-4636-99]("http://www.symantec.com/security_response/writeup.jsp?docid=2004-050511-4636-99")

---

### Post by Interpreter on 2008-10-09
](*,)[-X

*need to resist the urge to ...
.....

---

### Post by Terry S on 2008-10-09
> **Interpreter said:**
> Well I'm by all means a pacifistic person but for that post there I feel the urgent need to !$%?& you.
Wow Id love to insult you here but I fear the mods will end up banning me for that.
What a friggin con man you are. 
If your initial post wasnt supposed to sound like you'd fear that you'd been ATTACKED BY A VIRUS then I dunno what Im reading wrong.

(I mean common look at the thread name for christ's sake)

I'll leave this thread at once, cuz arguing would result in me calling you animal names.

Apologies if you feel even more attacked now but I am now left with the impression that you're "some kiddo bored at school provoking random folks on help boards".



Bye.

There is a G in frigging, an apostrophe in wasn't, another one in I'm and Christ is a proper name therefore requires a capital letter.
That my man was provoking a random person the rest was seeking assistance. If these forums affect you so badly you really should consider quiting them.

---

### Post by Terry S on 2008-10-09
> **jerome1232 said:**
> You posted from Terry S, quoting a post by tajs, saying it was your post. Perhaps I misunderstood and you weren't saying the post by tajs was your original post.



No problem. My name is Terry S and my email begins tajs. 

Sharply spotted though.:)

---

### Post by Terry S on 2008-10-09
> **Sub101 said:**
> Firstly IF the OP has two accounts the Forum Staff will know as they log IP's.

Secondly im amazed at the response this post has received. Being treated with such hostility. Admins have posted in this thread which surely is enough of a blessing for others.

To the OP. I would suggest the comment Sef made would be most likely and that has coursed the message you sent to another to appear to have a virus. Or you have forwared a message/attachment which did have a virus. 

And the issue regarding taking a long time to shut down. I had the same issue recently but on the next update it resolved itself. I did not do anything to fix it it just did. So maybe wait till new updates and see if that resolves it.

Thanks for you reply. I am glad somebody else thinks the replies a little hostile I thought I was been a overly sensitive:).

If the attachments I sent via email were the problem would not the virus checker I installed today have found them?

I was interested to hear you had similar shut down problems. I have received a couple of system updates since and the problem is still there. I think I will go with the reinstall.

Once again thanks

---

### Post by Interpreter on 2008-10-09
Please keep the arguing aimed as to whether or not the Virus attack thing is possible, not whether I sometimes lose my temper and then fail at a foreign language, Im sure that's normal adn to some extend OK.

Apart from doubting that you're downright honest about your account(s) I still dont get why you'd shout out "Virus attack" loud and wonder why I and othres think that you might actually be rambling about viri and not ..panties or whatever..

Maybe you're just new to "the internets" or whatnot I don't know and in the end it does not make a difference, but I wont "calm down and consider not posting here" if I actually enjoy "giving and receiving" of knowledge.

If someone talks about a virus attack I google abit and think about it and ....then I fail and notice that that person claims to not talk about an infection at all despite introducing me to his virus popups virus-like side effects and virus notifications in a contacts email, hell I start to think that someone is making fun of my efforts to join this board's community and noticing that youre using 2 accounts adds to that.

Hope that was a more polite way of expressing the not so polite first reaction.
Sry.
Now better explain yerself ;)

---

### Post by AlexBellisBrown on 2008-10-09
Perhaps now would be a good time for the mods to close this thread? *cough*

---

### Post by imperius69 on 2008-10-09
well, this topic brought me a question.

my question is if i receive a infected email, my Linux box wont get harmed, but how can i protect my friends from my TB from sending infected emails to them?

---

### Post by hyper_ch on 2008-10-09
> **Sub101 said:**
> And the flaming title? I do not consider 'virus attack' to be a flame. How can it be? It isn't 'Ubuntu security is rubbish as I got a virus'.
There's a difference between those two? Not really if you look at it in context ;)

---

### Post by Terry S on 2008-10-09
> **AlexBellisBrown said:**
> Perhaps now would be a good time for the mods to close this thread? *cough*

As the original poster I tend to agree. 

However, if the mention of Virus and Linux in the same sentence evokes such hostility maybe there should be a much wider debate to find out why.

I have been a Windows user for years and found Ubuntu quite recently. I was so impressed with Ubuntu I switched totally and permanently and I believe Ubuntu, vulnerable to virus attack or not, is streets ahead of Windows what ever the version. What I find hard to understand is why some people cannot/will not accept Linux/Ubuntu might be or will, some time in the future, be vulnerable to virus attack. 

Linux/Ubuntu is no less a a brilliant operating system just because it might have that vulnerability. The time to have such a debate is now not when the first 'in the wild' virus hits home and sets back the uptake of Linux Worldwide.

Speech over

---

### Post by Tomatz on 2008-10-09
> **Terry S said:**
> if the mention of Virus and Linux in the same sentence evokes such hostility


Oh and didn't you know it....

> I have been a Windows user for years and found Ubuntu quite recently

Hang on.... Thought you only "found" ubuntu/linux recently? How did you know that virus and linux in the same sentence "evokes such hostility"?



[EDIT]

It isn't the fact you said your system was infected, it was the blatantly naive way you went about it. You could have at least lied about a virus that could actually infect your system in the first place?

---

### Post by AlexBellisBrown on 2008-10-09
> **Tomatz said:**
>  it was the blatantly stupid way you went about it. 

No need to be so harsh, surely? Cant you people just let it drop?

---

### Post by Tomatz on 2008-10-09
> **AlexBellisBrown said:**
> No need to be so harsh, surely? Cant you people just let it drop?

Ok stupid was harsh so i edited it. ;)

It's just an annoying time wasting thread :(

---

### Post by AlexBellisBrown on 2008-10-09
Then lets all stop responding to it and let it die into the depths of the forums, this thing has already racked up over 1000 views!!!

---

### Post by Tomatz on 2008-10-09
> **AlexBellisBrown said:**
> Then lets all stop responding to it and let it die into the depths of the forums, this thing has already racked up over 1000 views!!!

Alexis, you are a legend!


:popcorn:

---

### Post by hyper_ch on 2008-10-09
now it's definitively confirmed that tajs / terry s is the same person.

---

### Post by Tomatz on 2008-10-09
> **hyper_ch said:**
> now it's definitively confirmed that tajs / terry s is the same person.

Yup hopefully someone will do something about it.

---

### Post by AlexBellisBrown on 2008-10-09
> **Tomatz said:**
> Alexis, you are a legend!

Thats what she said!

:popcorn: Totally inappropriate... I apologize. Thank you sir.

---

