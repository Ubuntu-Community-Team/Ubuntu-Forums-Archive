---
title: "Thunderbird does not start after upgrading to 9.10"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by grr51 on 2009-10-30
Hi,

I just upgraded from 9.04 to 9.10 and now Thunderbird does not start any more.
When I click on the applet, "Starting Mozilla Thunderbird" is briefly displayed at the bottom of the page and then disappears.  I rebooted with no effect.  I re-installed the packahe and that did not resolve the problem either.
All the other applications are working fine.

Any suggestion of how to resolve this nagging problem will be welcomed.

Thanks,

Gaétan

---

### Post by grr51 on 2009-10-31
> **grr51 said:**
> Hi,

I just upgraded from 9.04 to 9.10 and now Thunderbird does not start any more.
When I click on the applet, "Starting Mozilla Thunderbird" is briefly displayed at the bottom of the page and then disappears.  I rebooted with no effect.  I re-installed the packahe and that did not resolve the problem either.
All the other applications are working fine.

Any suggestion of how to resolve this nagging problem will be welcomed.

Thanks,

Gaétan

Problem soved. Refer to posting by "nanotube" copied below for reference:

 				 				**Re: Thunderbird won't start after install** 			
 			 			 		   		 		 		hrm apparently thunderbird still depends on libstdc++5

but karmic has removed this older library from the official repos.

so, grab the .deb of libstdc++5 from the jaunty repos, here:
[http://packages.ubuntu.com/jaunty/libstdc++5](http://packages.ubuntu.com/jaunty/libstdc++5)

and install. that will fix you up.
 		                   		  		  		 		 			 				__________________
				[The Ubuntuzilla Project]("http://ubuntuzilla.sourceforge.net/")
[Dvorak Switching Guide]("http://wiki.df.dreamhosters.com/wiki/DvorakHowTo") | [Latest Ubuntu Chronicles]("http://wiki.df.dreamhosters.com/wiki/Ubuntu_Chronicles_Intrepid") | [Ubuntu Forums FAQ]("http://wiki.df.dreamhosters.com/wiki/Ubuntu_Forums_FAQ")
[How to ask good questions]("http://www.catb.org/%7Eesr/faqs/smart-questions.html")

---

### Post by mvelte54 on 2009-11-01
He's right...
I upgraded to Karmic Koala 2 days ago then on a whim ran computer janitor. Opps Thunderbird quit loading for me. Did a little research and found this and ran it and bingo I'm back in business. You guys ROCK!

And as for Karmic Koala... I love it! Sure there are going to be little snags here and there but what new system doesn't have some, nothing is going to be to everyone's liking straight off the shelf. 
Quit your whining and get your hands dirty do a little research if you find a work a round help another out and share.

---

### Post by Baasha on 2009-11-02
I upgraded to Karmic a couple of days ago and I have the same problem with TB.  I ran TB from the terminal and it said "error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory".  Checked in Synaptic and it said I do have it.  So then I re-installed the lib from the source given above but TB is still dead in the water with the same error message.

Does anyone have any ideas how to get this going?

PS: I am running a AMD_64 OS.

---

### Post by Johnr123 on 2009-11-05
Thank you for the fix for ThunderBird not working after upgrade to Karmic. Much appreciated. It worked!

Cheers,
John

---

### Post by intrader on 2009-11-22
I have the same issue with 9.04. So I think that it is a problem in Thunderbird (version 2.0.0.23). I also installed the library but there was no change in thunderbird. From  the Terminal I don't get any error message.
The dependent library list is
libnspr4.so
libplc4.so
libplds4.so
libxpcom_core.so
And they are all installed. I don't know where the log files, so I can't tell why it is just not starting.
Help please

---

### Post by Johnr123 on 2009-11-22
Well I thought I was all fixed up (re: my above post) but after getting ThunderBird up and running again from the Karmic upgrade issue with it, ThunderBird became extremely slow.

 Im tired of trying to fix the problems the upgrade to Karmic created (I still have to fix a Wacom tablet problem), so I chose to migrate all my mail and folders over to Evolution. I'm glad I did. It is snappy and much more feature rich than ThunderBird. It took all of twenty minutes to migrate everything over and set up the accounts. 

John

---

