---
title: "Building My First Linux Machine"
date: 2010-02-17
forum: Hardware
---

### Post by fiftyfour123 on 2010-02-17
I currently host my website on my old PPC eMac. I'm just tired of the unreliability and slowness of it. At first i thought about building a hackintosh and installing Snow Leopard Server, but then I decided it would be cheaper and easier to just build a machine for linux. My main reason is that i want an Intel machine so i can host virtual machines. Also, whenever my eMac would lose internet connection for whatever reason, I wouldn't be able to remotely restart it. So here is a wishlist of what i would ideally like to have in the machine. Hopefully someone can point me in the right direction of what parts to buy and where i can get the best deals. I really don't want to spend over $200.

[LIST]
[*]Intel processor with 2+ GHz
[*]at least a 120 gb hard drive
[*]I guess 4 gb of ram so virtual machines won't slow down the whole computer
[*]At least 2 USB 2.0 Ports
[*]Don't need a CD Drive. I can install the OS off a USB drive (right?)
[*]A sound card so I can monitor the sound around the server
[*]And for the monitor i'm going to use a portable DVD player that has A/V inputs so i don't know it it would be better to just have A/V ports on the computer or to have a VGA or DVI port and just get a cable to convert to A/V cables
[/LIST]

Also, i want to be able to power on the machine remotely if it isn't on. I think that's called out-of-band management, but i'm not sure. I know it's called Lights-out Management on a Mac.

EDIT: Oops, I forgot that i'll need a wireless card. Unless out-of-band management requires ethernet which is ok too.

EDIT2: I also forgot to say that i'm going to be using Ubuntu Desktop on the machine because i don't feel comfortable without a GUI in the server edition. The server will be in a secure location so security really isn't too much of an issue.

Thanks for any help!

---

### Post by fiftyfour123 on 2010-02-17
anyone?

---

### Post by Richard1979 on 2010-02-17
Not sure how much of that you'd be able to pick up for $200. I'm guessing that's about £150 which isn't a lot for a PC.
I'd recommend looking on ebay or something.

> Also, i want to be able to power on the machine remotely if it isn't on.
Wake on LAN, that's called.
Can be done from the Terminal if I remember correctly.

Also if you're going to boot off USB, make sure the BIOS can boot from USB (most ones can if they are newer than 2004 or so).
You'll also need a Linux or Windows machine to create the USB image.

---

### Post by fiftyfour123 on 2010-02-17
> **Richard1979 said:**
> Not sure how much of that you'd be able to pick up for $200. I'm guessing that's about £150 which isn't a lot for a PC.

What do you think I would have to pay to do what I want to do?


> **Richard1979 said:**
> Wake on LAN, that's called.
Can be done from the Terminal if I remember correctly.

Isn't Wake On LAN only for waking from sleep, not powering on?

> **Richard1979 said:**
> Also if you're going to boot off USB, make sure the BIOS can boot from USB (most ones can if they are newer than 2004 or so).
You'll also need a Linux or Windows machine to create the USB image.

Why can't I just extract the install image to a partition on a usb drive and boot from that?

---

### Post by hxcobd on 2010-02-17
My secret weapon for appallingly cheap desktop PCs:

[http://www.ascendtech.us/](http://www.ascendtech.us/)

Go to Desktops -> Intel Complete Systems w/ No OS

Systems starting at $100. Brand new.

I've owned 2 desktops from them, both worked great up until the day I replaced them. I'm sure they use ridiculously cheap/crappy parts, but for $100 for a brand new computer, who can complain?

*edit - I should add that I used linux and BSD distros on both systems and never had any hardware issues. Obviously it's going to vary depending on every system, but 2/2 works for me!

---

### Post by fiftyfour123 on 2010-02-17
> **hxcobd said:**
> My secret weapon for appallingly cheap desktop PCs:

[http://www.ascendtech.us/](http://www.ascendtech.us/)

Go to Desktops -> Intel Complete Systems w/ No OS

Systems starting at $100. Brand new.

I've owned 2 desktops from them, both worked great up until the day I replaced them. I'm sure they use ridiculously cheap/crappy parts, but for $100 for a brand new computer, who can complain?

*edit - I should add that I used linux and BSD distros on both systems and never had any hardware issues. Obviously it's going to vary depending on every system, but 2/2 works for me!

wow, that looks awesome. I'm gonna consider them. thanks

---

### Post by fiftyfour123 on 2010-02-18
What I think i'm gonna do is just buy parts from newegg.com and build it myself. At first i figured i would use a micro ATX motherboard so I came up with these parts:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16813131615](http://www.newegg.com/Product/Product.aspx?Item=N82E16813131615)
[http://www.newegg.com/Product/Product.aspx?Item=N82E16819116265](http://www.newegg.com/Product/Product.aspx?Item=N82E16819116265)
[http://www.newegg.com/Product/Product.aspx?Item=N82E16820141337](http://www.newegg.com/Product/Product.aspx?Item=N82E16820141337)

Would those all work together? I'm not really sure what I would need regarding the power supply.

I also found on newegg that they sell motherboard/CPU combos for much cheaper and they all use Intel Atom processors. I don't really know much about those, so what would i expect with them? For example this one :[http://www.newegg.com/Product/Product.aspx?Item=N82E16813153143](http://www.newegg.com/Product/Product.aspx?Item=N82E16813153143)

I picked that one because of the good reviews and it can take 4 gb of ram which I want for hosting virtual machines. Unless i'd be able to do it with 2 gb. Is there any reason most of those Motherboard/CPU combos can only handle 2 gb of ram?

If those combo motherboards will be powerful enough to host a website and some virtual machines it seems obvious that I should go with one of those, right? What do you think?

---

### Post by hxcobd on 2010-02-18
Intel Atom are the processors found in most modern netbooks.

They're incredibly underpowered and not really suitable for anything CPU-intensive at all.

---

### Post by fiftyfour123 on 2010-02-18
> **hxcobd said:**
> Intel Atom are the processors found in most modern netbooks.

They're incredibly underpowered and not really suitable for anything CPU-intensive at all.

So, does my initial configuration look like with will work with ubuntu? Also, what kind of power supply would i need. I read somewhere that 300 W is sufficient. Does that sound right?

---

### Post by fiftyfour123 on 2010-02-20
Ok, I think i've finalized my configuration. However I'm new to building computers so I'm not sure if all this stuff is compatible with each other and with Ubuntu. Heres what I picked:

Motherboard: [http://www.newegg.com/Product/Product.aspx?Item=N82E16813131615](http://www.newegg.com/Product/Product.aspx?Item=N82E16813131615)
Processor: [http://www.newegg.com/Product/Product.aspx?Item=N82E16819116265](http://www.newegg.com/Product/Product.aspx?Item=N82E16819116265)
Memory: [http://www.newegg.com/Product/Product.aspx?Item=N82E16820141337](http://www.newegg.com/Product/Product.aspx?Item=N82E16820141337)
Hard Drive: [http://www.newegg.com/Product/Product.aspx?Item=N82E16822148397](http://www.newegg.com/Product/Product.aspx?Item=N82E16822148397)
Power Supply: [http://www.newegg.com/Product/Product.aspx?Item=N82E16817338031](http://www.newegg.com/Product/Product.aspx?Item=N82E16817338031)
Case: [http://www.newegg.com/Product/Product.aspx?Item=N82E16811154094](http://www.newegg.com/Product/Product.aspx?Item=N82E16811154094)

Thanks for any help.

---

### Post by bpalone on 2010-02-20
Unless you are getting a lot of traffic to your web site, an Atom processor and board will work.  I have been using a single core one with 1 gig of memory for 6 or 8 months now.  It has been doing fine, but very low traffic.  Of course, it replaced an old AMD K6 333, so most anything would appear to be grand.  

You might want to consider a dual core ATOM, as if I remember correctly it is only about $20 more from NewEgg.  I am guessing that your limiting factor is going to be your upload speed to the net.  It doesn't take much CPU power to serve up simple web pages.  If you start using and doing heavy data base and/or heavy graphics, then you need a bit more horse power.  So, another reason for a dual core.

If I remember correctly, I had about $70 into my single core and 1 gig.  I spent that much or more for a power supply.  Had an old case that I modded to accept the mother board.  I also had a number of old IDE hard drives lying around that were large enough for the job.

Have fun putting it together.

---

### Post by fiftyfour123 on 2010-02-20
The thing is I'm not just hosting web pages. I also want to host virtual machines. Would an Atom processor be able to handle that? That's also the reason I'm going for the 4 gigs of memory, I don't want the virtual machines to slow down the whole computer, unless you think 2 would be sufficient so I can save 50 bucks.

---

### Post by HarshReality on 2010-02-20
> **fiftyfour123 said:**
> The thing is I'm not just hosting web pages. I also want to host virtual machines. Would an Atom processor be able to handle that? That's also the reason I'm going for the 4 gigs of memory, I don't want the virtual machines to slow down the whole computer, unless you think 2 would be sufficient so I can save 50 bucks.

No disrepect but hosting VM for multiple access and using an atom to do it has got to be some sort of a joke.

---

### Post by fiftyfour123 on 2010-02-20
> **HarshReality said:**
> No disrepect but hosting VM for multiple access and using an atom to do it has got to be some sort of a joke.

Haha, i totally agree. I just did some research about that. I'm definitely leaning away from the Atom processor but the price is so much more attractive. But i'll probably just go with an Intel Celeron E3200.

Back to my earlier question: Will all this stuff work together nicely on Ubuntu?

Motherboard: [http://www.newegg.com/Product/Product.aspx?Item=N82E16813131615](http://www.newegg.com/Product/Product.aspx?Item=N82E16813131615)
Processor: [http://www.newegg.com/Product/Product.aspx?Item=N82E16819116265](http://www.newegg.com/Product/Product.aspx?Item=N82E16819116265)
Memory: [http://www.newegg.com/Product/Product.aspx?Item=N82E16820141337](http://www.newegg.com/Product/Product.aspx?Item=N82E16820141337)
Hard Drive: [http://www.newegg.com/Product/Product.aspx?Item=N82E16822148397](http://www.newegg.com/Product/Product.aspx?Item=N82E16822148397)
Power Supply: [http://www.newegg.com/Product/Product.aspx?Item=N82E16817338031](http://www.newegg.com/Product/Product.aspx?Item=N82E16817338031)
Case: [http://www.newegg.com/Product/Product.aspx?Item=N82E16811154094](http://www.newegg.com/Product/Product.aspx?Item=N82E16811154094)

---

### Post by v1ad on 2010-02-20
AMD :] for the lower prices they usually provide better speeds.

[http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010340343+4026+50001028&QksAutoSuggestion=&ShowDeactivatedMark=False&Configurator=&Subcategory=343&description=&Ntk=&CFG=&SpeTabStoreType=&srchInDesc=](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010340343+4026+50001028&QksAutoSuggestion=&ShowDeactivatedMark=False&Configurator=&Subcategory=343&description=&Ntk=&CFG=&SpeTabStoreType=&srchInDesc=)



better yet a server processor 
[http://www.newegg.com/Product/Product.aspx?Item=N82E16819105259](http://www.newegg.com/Product/Product.aspx?Item=N82E16819105259)
[http://www.newegg.com/Product/Product.aspx?Item=N82E16813131613](http://www.newegg.com/Product/Product.aspx?Item=N82E16813131613)

---

### Post by fiftyfour123 on 2010-02-20
> **v1ad said:**
> AMD :] for the lower prices they usually provide better speeds.

[http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010340343+4026+50001028&QksAutoSuggestion=&ShowDeactivatedMark=False&Configurator=&Subcategory=343&description=&Ntk=&CFG=&SpeTabStoreType=&srchInDesc=](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010340343+4026+50001028&QksAutoSuggestion=&ShowDeactivatedMark=False&Configurator=&Subcategory=343&description=&Ntk=&CFG=&SpeTabStoreType=&srchInDesc=)

I've thought about that. But if I went with AMD, would I be able to use a virtual machine hosted on the AMD machine on my Intel Mac? Would there be any compatibility issues?

---

### Post by v1ad on 2010-02-20
there shouldn't be any issues since bios or virtual bios detects the cpu on startup. your virtual box should take care of any problems.

also the server processors have a lot higher reliability then regular processors

---

### Post by fiftyfour123 on 2010-02-20
> **v1ad said:**
> there shouldn't be any issues since bios or virtual bios detects the cpu on startup. your virtual box should take care of any problems.

Awesome. I might go with AMD then, since the processors and motherboards are cheaper. Do you think there would ever be an instance were i may have wished i got an intel processor?

---

### Post by v1ad on 2010-02-20
only if you want to game and get the i7. but overall on the lower end processing power i think you will get a lot better performance for the price. if you look at my above post i posted a link for a server processor. i think that 1 will make you more happy. and will not go out on you. i used intel and amd. the only time i preferred Intel was when the i7 came out.

---

### Post by bpalone on 2010-02-20
> **fiftyfour123 said:**
> The thing is I'm not just hosting web pages. I also want to host virtual machines. Would an Atom processor be able to handle that? That's also the reason I'm going for the 4 gigs of memory, I don't want the virtual machines to slow down the whole computer, unless you think 2 would be sufficient so I can save 50 bucks.


From this I assume that you intend to host some virtual machine servers to allow friends access to your high speed connection for their own websites.  Or, you are going to be experimenting with different things out to the web.  In either case, I would then recommend going with more power in the CPU department.  As someone stated, don't be afraid of the AMD CPUs.  I use them in 99.99% of my desktop builds.  You can get a bit more bang for your buck with them and they do just fine running virtual machines.  I personally haven't tried running a VM on an Atom, but I have read on some threads where people have.  This is being typed on a laptop powered by a 1.4 GHZ Celeron and I run VirtualBox on it for some Windows apps that I need.  It does OK, it isn't as fast as my desk tops, but it gets the job done, you just have to be a bit patient some times.

But, from what you have said, I would go with a higher horse power build.  I didn't look at the hardware you are proposing, but in general if you don't get bleeding edge you will be OK.  I tend to go with Nvidia video, etc as they tend to be a bit more Linux friendly.  ATI has been improving and from posts I've seen they not to bad now.  Do a search here on the forums for your NIC, your Video and your Sound Card.  That will give you a good idea of how easy or hard they will be to deal with.

---

### Post by fiftyfour123 on 2010-02-20
> **v1ad said:**
> AMD :] for the lower prices they usually provide better speeds.

[http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010340343+4026+50001028&QksAutoSuggestion=&ShowDeactivatedMark=False&Configurator=&Subcategory=343&description=&Ntk=&CFG=&SpeTabStoreType=&srchInDesc=](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010340343+4026+50001028&QksAutoSuggestion=&ShowDeactivatedMark=False&Configurator=&Subcategory=343&description=&Ntk=&CFG=&SpeTabStoreType=&srchInDesc=)



better yet a server processor 
[http://www.newegg.com/Product/Product.aspx?Item=N82E16819105259](http://www.newegg.com/Product/Product.aspx?Item=N82E16819105259)
[http://www.newegg.com/Product/Product.aspx?Item=N82E16813131613](http://www.newegg.com/Product/Product.aspx?Item=N82E16813131613)

I like those two choices, but Are they compatibile? The processors isnt listed on the motherboard page.

---

### Post by Minotauraus on 2010-02-20
[http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=30000007+4017&QksAutoSuggestion=&ShowDeactivatedMark=False&Configurator=&Subcategory=-1&description=&Ntk=&CFG=&SpeTabStoreType=&srchInDesc=](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=30000007+4017&QksAutoSuggestion=&ShowDeactivatedMark=False&Configurator=&Subcategory=-1&description=&Ntk=&CFG=&SpeTabStoreType=&srchInDesc=)

Also, if you have some wood and nails lying around, you could save a few bucks by making your own tower/cabinet. You then have freedom to chose the layout of your internal components based on your needs.

---

### Post by fiftyfour123 on 2010-02-20
> **Minotauraus said:**
> [http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=30000007+4017&QksAutoSuggestion=&ShowDeactivatedMark=False&Configurator=&Subcategory=-1&description=&Ntk=&CFG=&SpeTabStoreType=&srchInDesc=](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=30000007+4017&QksAutoSuggestion=&ShowDeactivatedMark=False&Configurator=&Subcategory=-1&description=&Ntk=&CFG=&SpeTabStoreType=&srchInDesc=)

Also, if you have some wood and nails lying around, you could save a few bucks by making your own tower/cabinet. You then have freedom to chose the layout of your internal components based on your needs.

Ehh, I think I'd rather just buy the parts separately.

> **v1ad said:**
> AMD :] for the lower prices they usually provide better speeds.

[http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010340343+4026+50001028&QksAutoSuggestion=&ShowDeactivatedMark=False&Configurator=&Subcategory=343&description=&Ntk=&CFG=&SpeTabStoreType=&srchInDesc=](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010340343+4026+50001028&QksAutoSuggestion=&ShowDeactivatedMark=False&Configurator=&Subcategory=343&description=&Ntk=&CFG=&SpeTabStoreType=&srchInDesc=)



better yet a server processor 
[http://www.newegg.com/Product/Product.aspx?Item=N82E16819105259](http://www.newegg.com/Product/Product.aspx?Item=N82E16819105259)
[http://www.newegg.com/Product/Product.aspx?Item=N82E16813131613](http://www.newegg.com/Product/Product.aspx?Item=N82E16813131613)

I like those two choices, but Are they compatibile? The processors isnt listed on the motherboard page.

---

### Post by bpalone on 2010-02-20
If you use an AMD processor you need to use an AMD motherboard.  They have different pin outs and require some differences in the BIOS.  The one processor I looked at was the Opteron and it was an AM2 socket, so an AMD AM2 socket board should work.

---

### Post by fiftyfour123 on 2010-02-20
> **bpalone said:**
> If you use an AMD processor you need to use an AMD motherboard.  They have different pin outs and require some differences in the BIOS.  The one processor I looked at was the Opteron and it was an AM2 socket, so an AMD AM2 socket board should work.

But the motherboard doesn't list Opteron as being a compatible cpu type

---

### Post by bpalone on 2010-02-20
Go to the mother boards manufactures web site and check for compatible CPUs for that specific board.  The manufacturer site usually has far more extensive list than you will find listed by a retailer.  Their list is usually larger than is listed in their manual.  The other thing is check the core code name, sometimes they list them that way.

---

### Post by fiftyfour123 on 2010-02-20
Ok, I have a new list now:

Motherboard: [http://www.newegg.com/Product/Product.aspx?Item=N82E16813131613](http://www.newegg.com/Product/Product.aspx?Item=N82E16813131613)
CPU: [http://www.newegg.com/Product/Product.aspx?Item=N82E16819103688](http://www.newegg.com/Product/Product.aspx?Item=N82E16819103688)
Memory: [http://www.newegg.com/Product/Product.aspx?Item=N82E16820141337](http://www.newegg.com/Product/Product.aspx?Item=N82E16820141337)
Hard Drive: [http://www.newegg.com/Product/Product.aspx?Item=N82E16822148397](http://www.newegg.com/Product/Product.aspx?Item=N82E16822148397)
Power Supply: [http://www.newegg.com/Product/Product.aspx?Item=N82E16817338031](http://www.newegg.com/Product/Product.aspx?Item=N82E16817338031)
Case: [http://www.newegg.com/Product/Product.aspx?Item=N82E16811154094](http://www.newegg.com/Product/Product.aspx?Item=N82E16811154094)

I would really appreciate it if someone could take the time to ensure that all of those will work nicely together (and with Ubuntu).

Also, to be able to use all 4 gigs of RAM, will I have to install the 64-bit version of Ubuntu? I would much rather just use 32-bit so I don't have to deal with finding 64-bit versions of everything I use.

Thanks

---

### Post by bpalone on 2010-02-20
I didn't look at the power supply, but I assume you got enough watts.

You might want to check if the memory you have selected works with that MB.  ASUS can be finicky at times about memory make.  The ASUS site usually keeps a decent list of approved memory for each MB.  I have gotten by with non named memory, but I have also seen where people have had trouble and changing to approved memory cleared the problem.  I use ASUS AMD boards for most all of my desk top builds.  Have one setting at home waiting to be put together in fact.  I usually just buck up and buy approved memory to limit issues on start up.

As for the 4 gig of memory, 32 bit will only see about 3.6 or so. It won't hurt anything by not using that bit of memory.  I usually just go with 3 gig and forget about it, which with your MB isn't an option (it is either 1, 2, or 4).  Have not had a memory issue with that much even with a couple VMs running.  When setting up your VMs, be stingy with the memory.  I don't what you are going to be running in your VMs, but you can always increase it until you find the sweet spot.  With Win 2K I find that 512K seems to work just great and in most instances I could go less.  I have one set up with 1 gig and I don't notice any great difference in speed etc.  

Have fun putting it all together.  Hope you have a trouble free assembly and start up.

---

### Post by fiftyfour123 on 2010-02-20
> **bpalone said:**
> I didn't look at the power supply, but I assume you got enough watts.

You might want to check if the memory you have selected works with that MB.  ASUS can be finicky at times about memory make.  The ASUS site usually keeps a decent list of approved memory for each MB.  I have gotten by with non named memory, but I have also seen where people have had trouble land changing to approved memory cleared the problem.  I use ASUS AMD boards for most all of my desk top builds.  Have one setting at home waiting to be put together in fact.  I usually just buck up and buy approved memory to limit issues on start up.

As for the 4 gig of memory, 32 bit will only see about 3.6 or so.  I usually just go with 3 gig and forget about it.  Have not had a memory issue with that much even with a couple VMs running.  When setting up your VMs, be stingy with the memory.  I don't what you are going to be running in your VMs, but you can always increase it until you find the sweet spot.  With Win 2K I find that 512K seems to work just great and in most instances I could go less.  I have one set up with 1 gig and I don't notice any great difference in speed etc.  

Have fun putting it all together.  Hope you have a trouble free assembly and start up.

You think 300 Watts for the power supply will be enough? Also, I'll look into the memory. I think i'm just going to go with 3 gigs to save myself the trouble. Thanks for all the help.

---

### Post by bpalone on 2010-02-21
Use NewEggs Power Supply Calculator: [http://educations.newegg.com/tool/psucalc/index.html]("http://educations.newegg.com/tool/psucalc/index.html")

That will give you a good idea of what you will need. You want some buffer to handle everything at once, so chose accordingly.  Another thing is that all power supplies are not created equal.  Some deliver as advertised and some do not.  Be sure to read the reviews and pick one that isn't getting a lot of bad comments.

---

### Post by bpalone on 2010-02-21
Just happened to think of this.  You can download the manual for the Mother Board from ASUS' web site.  That will give a lot of information before you order or get it. It will also tell you if you can do just the 3 gig or not.  I am guessing that it will be stepped in this manner 256, 512, 1 gig, 2 gig,and 4 gig.  It won't hurt anything by putting 4 gig in and 32 bit only seeing what it does.

---

### Post by fiftyfour123 on 2010-02-21
Ok cool. Thanks for all the help. I'll post back once I build it, hopefully with good news.

---

### Post by fiftyfour123 on 2010-03-05
Good news! I put everything together and installed ubuntu and everything seems to be working fine. The only problem i had was that the opening in the case for the power supply was too big. however, i made some brackets to hold it in place. thanks for all the help!

---

### Post by bpalone on 2010-03-06
Glad it all works.  Sounds like you enjoyed the project.

---

