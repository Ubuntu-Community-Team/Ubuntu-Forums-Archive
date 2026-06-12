---
title: "How do I install my Canon PIXMA iP1700 printer to Ubuntu 64-bit?"
date: 2021-11-17
forum: Hardware
---

### Post by hereamack on 2021-11-17
I purchased a Canon PIXMA iP1700 printer in late 2006.

At the time, I had a 32-bit computer with Microsoft Windows XP 32-bit installed on it.

Now, I have a 64-bit computer with Ubuntu 64-bit installed on it.

I can't print to my Canon PIXMA iP1700 printer from this installation of Ubuntu 64-bit on my 64-bit computer.

I would really appreciate it if somebody could please provide me with instructions to install my Canon PIXMA iP1700 printer on Ubuntu 64-bit so that I can print to it.

Thanks a lot for any assistance you can provide.

---

### Post by TheFu on 2021-11-17
I assume you've run **system-config-printer** and connected the printer, then tried to add it already?  For supported printers, this is a 20 second setup and they "just work."  My brother and samsung printers work that way.

My mom had a similar model printer in 2010 - perhaps an ip1800?  It was a gift. Her WinXP OS install got hacked and she asked me for help. I moved her to Lubuntu 10.04 and we got everything working except printing with that printer.  Her printer was $50 and the ink was going to cost her $30+/yr no matter what. Ink dries out.  

There was/is a European company that makes Linux drivers for the printer - $50.  I understand they are great. [https://www.turboprint.info/printer_Canon_PIXMA_iP1700.html](https://www.turboprint.info/printer_Canon_PIXMA_iP1700.html)  The other option is here: [https://tutorialforlinux.com/2021/01/16/printer-canon-ip1700-ip1800-driver-ubuntu-installation/](https://tutorialforlinux.com/2021/01/16/printer-canon-ip1700-ip1800-driver-ubuntu-installation/) which uses GutenPrint, whatever that is.

I suggested that a cheap laser printer with native Linux support would be a better solution, since laser toner doesn't dry out and 2K - 10K page cartridges are fairly cheap, but it was her choice.  Natively supported hardware is just so much easier, not just when we first connect it, but for the next 10+ yrs with each OS upgrade. There just aren't the hassles that unsupported devices have.  She decided a new laser printer would be the best choice and for the few times she needed color prints, she could visit a local print-shoppe or a local relative to print.  I bought her a Brother laser printer - think it was $80 at the time and an 8K pg toner cartridge. 

She gave the PIXMA to a granddaughter who needed a great color printer and ran Windows.

---

### Post by hereamack on 2021-11-17
> **TheFu said:**
> I assume you've run **system-config-printer** and connected the printer, then tried to add it already?  For supported printers, this is a 20 second setup and they "just work."  My brother and samsung printers work that way.


Thanks a lot for your assistance.

It's not right that application developers,  such as operating system developers, were happy to consign many tens of  millions of computers, printers and scanners, that were designed to work with  32-bit operating systems, to the rubbish dump as a  result of changing the applications they develop to 64-bit applications,  such as 64-bit operating systems.  That's a bare minimum of 100 million computers, 100 million printers and about 25 million scanners all going to the rubbish dump even though they all still work perfectly well.

---

### Post by TheFu on 2021-11-17
> **hereamack said:**
> Thanks a lot for your assistance.

It's not right that application developers,  such as operating system developers, were happy to consign many tens of  millions of computers, printers and scanners, that were designed to work with  32-bit operating systems, to the rubbish dump as a  result of changing the applications they develop to 64-bit applications,  such as 64-bit operating systems.  That's a bare minimum of 100 million computers, 100 million printers and about 25 million scanners all going to the rubbish dump even though they all still work perfectly well.

It wasn't the developers. It was the companies they work at.  The upper management has to make choices for financial reasons all the time and working on software that cannot lead to a new sale isn't what printer companies do.

However you got the Canon printer, it was under your control, so you share some of the blame.  Canon has never made Linux drivers available for that model, so they didn't set any expectations there would ever be any drivers.

There are many security issues with 32-bit hardware and software. At some point, abandoning that architecture is a kindness.  OTOH, I drive a 21 yr old car which got a safety recall just over a year ago for airbag fixes. The dealer fixed it for free.  But cars aren't $50 printers.

---

### Post by hereamack on 2021-11-17
> **TheFu said:**
> It wasn't the developers. It was the companies they work at.  The upper management has to make choices for financial reasons all the time and working on software that cannot lead to a new sale isn't what printer companies do.


Why would you think that I was referring to application developers who are employees  instead of application developers which are corporations?  Micrsoft is an  application developer.

I don't share any of the blame for the fact that I can't use my Canon printer or Canon scanner with Linux-based Ubuntu.  Canon doesn't even provide drivers for Microsoft Windows 7 for my Canon printer and Canon scanner, let alone Linux-based operating systems like Ubuntu.

Whitewashing the scrapping of a minimum of  225 million pieces of hardware, that all work perfectly well, like you  are doing is unconscionable.

---

### Post by TheFu on 2021-11-17
> **hereamack said:**
> Why would you think that I was referring to application developers who are employees  instead of application developers which are corporations?  Micrsoft is an  application developer.

Why wouldn't you think it was a person?  A developer us a human. It is a job title. Guess it depends on your background.

> **hereamack said:**
> I don't share any of the blame for the fact that I can't use my Canon printer or Canon scanner with Linux-based Ubuntu.  Canon doesn't even provide drivers for Microsoft Windows 7 for my Canon printer and Canon scanner, let alone Linux-based operating systems like Ubuntu.

If you wanted support for Linux, shouldn't you have bought a printer with that support?  That's the best way to get more hardware to support Linux. We call it voting with our money. Every time someone buys hardware without Linux support, they are working against Linux.

> **hereamack said:**
> Whitewashing the scrapping of a minimum of  225 million pieces of hardware, that all work perfectly well, like you  are doing is unconscionable.
Nothing is scrapped.  If you were running the same old OS, then it would keep working until the hardware failed or printer supplies stopped being made.

Software isn't like hardware. Sorry.  Do you give your work away for free?  Software developers like to be paid - the individuals - at their day jobs.  In the evenings, they may choose to give their effort away.

BTW, I have lots and lots of very old hardware that still works, because I was careful when buying it to ensure it was supported by linux without any proprietary drivers needed. I'm using an IBM 101m keyboard from the mid-1990s and a mouse from 2000. I have some hardware, usually bought on a whim, that isn't supported.  A scanner, old inkjet printer, a logitech C-series mouse - not supported.

It is a never-ending challenge for everyone.

---

### Post by hereamack on 2021-11-17
Here's the reality:

The information technology industry, including computer manufacturers, application developers (e.g. Microsoft) and peripheral manufacturers, is a gigantic, confused mess, which is designed to manipulate consumers and extract as much money from them as possible.  At this point, this is undeniable.

---

### Post by TheFu on 2021-11-17
> **hereamack said:**
> Here's the reality:

The information technology industry, including computer manufacturers, application developers (e.g. Microsoft) and peripheral manufacturers, is a gigantic, confused mess, which is designed to manipulate consumers and extract as much money from them as possible.  At this point, this is undeniable.

EVERY for-profit company is designed to extract as much money from customers as possible.  That's the world.  

Ever tried to pick out toilet paper?  There are 20 choices and the marketing is all crap.  If they really wanted to make it easy to select, there would be a sample next to each pack so we could feel the softness and thickness.  But they don't do that.  Why do we buy the $10 pak instead of the $6 pak? I'm so confused.

Or elsewhere in any grocery store.  There are lots of different options for canned beans, from $0.50/can to $2.50/can.  Why is that?  I'm so confused.

Or when I go to buy a car.  There are 50 choices.  They use all sorts of jargon that actually means nothing.  They are clearly trying to confuse me.

Or when we try to pick a car mechanic.  They are all similar, but different.  How can I be expected to pick the best one with the best value for my needs that is still convenient?  I'm so confused.

Just be thankful you don't have to deal with companies like Oracle or EMC or VMware that specifically look at complex pricing to maximize profits over helping more customers.  There are typically 2 prices for the same profit levels.  One is by selling to as many customers as possible, but with lower profit margins and the other is to sell for a premium price, but to fewer customers.  Less work, same profit with customers willing to pay.  Basically, that is the Apple hardware (iPhone and Mac) sales model.

A printer has been a 1-time purchase. There is very little incentive for a company to spend any effort on creating new drivers for later OSes.  OTOH, many Vista-64 drivers still work on Win10/11 (I heard).  I don't actually have Win10/11 here. I have a personal goal to never give any money to MSFT again in my life. I've never paid Apple for anything either.  At least not directly.  Of course, MSFT gets paid whenever we buy a camera or SD card or some printers since they have licenses for exFAT with agreements so those manufacturers get paid.

You and I won't change this. Even when I had my own consulting company and pushed clients towards Linux solutions, they would often pick a proprietary solution because they'd "heard of it" before. If I wanted the job, I needed to provide the client what they wanted.  Since I like to eat and have a house, I did that.  Being paid is good.

---

### Post by hereamack on 2021-11-17
> **TheFu said:**
> EVERY for-profit company is designed to extract as much money from customers as possible.  That's the world.

You're quite presumptuous.  How would you know that I'm not going to change the information technology industry?  You've never met me.

The only viable business model for application developers like Microsoft is to charge users of their applications a monthly subscription.  This is in the best interests of users, since the applications they use can then be supported on an ongoing basis, and it's in the best interests of application developers like Microsoft, since it provides them with a stable stream of revenue.

Anyway, regarding my problem with printing and scanning with my Canon scanner and printer on the Ubuntu 64-bit operating system, I'm going back to using Microsoft Windows 7 64-bit.  I'll install LibreOffice 64-bit for free.  I would have to be mad to go out and buy a new printer and scanner because I can't get my existing, perfectly good printer and scanner to work with Ubuntu.

I predict that in a year or two, Linux-based operating systems like Ubuntu will be even more user-friendly and I'll be able to easily print and scan with my Canon printer and scanner on the Ubuntu 64-bit operating system.

---

### Post by TheFu on 2021-11-17
> You're quite presumptuous. How would you know that I'm not going to change the information technology industry? You've never met me.

I've been around a very long time and have heard thousands of people make claims that never become true.  It isn't presumptuous at all. I'm not gullible.  The top 20 IT companies haven't changed how support works with 15 yr old hardware.  The newest companies have made it even worse, expecting us to replace hardware every 4 yrs.  I have a google phone. Within 3 yrs of my purchase, they stopped supporting it. It was the flagship phone at the time.  I own 2 chromebooks. Both have lost OS updates, but they also had the keyboards fail. Nothing wrong with the other parts, just the keyboard. Alas, the replace the keyboard is $30-$40 in hardware, but $100+ in labor.  I can buy a used chromebook for $75, so why would I pay $130 to change the keyboard for an unsupported device?

Printing is really easy in Linux, just with other printers.  It takes 20 seconds to setup already - if you have one of the 200+ supported printers.
While I hope you are right, 25 yrs in this industry has taught me that isn't practical.  Newer printers have a "zero-driver" model.  There's IPP for other printers, but the specific model you have isn't one of them.

I take it you didn't click either of the links my first post provided?  There's a point where either you want to print or you want to think you are right (and not print).  I was young and felt that way with an Epson printer.  It never worked. I gave it away and went without a printer at home for a few years.  For that period, I "was right" too.  Then I retired from work (very early) and needed to print tax forms.  I could have taken some PDF files to a local print shop or the local library and paid $0.10/page, but I was lazy, just started a business and needed to print legal documents for filing with the state.

But you don't need to believe me.

Good chat. Nice to see some different views on stuff, but I need to go pick out some TP. I'm so confused.

---

### Post by hereamack on 2021-11-17
You're so presumptuous.  I'd already read the first link you sent me and I visited the second link you sent me because I post in good faith, unlike you.

---

### Post by hereamack on 2021-11-17
> **TheFu said:**
> I've been around a very long time and have heard thousands of people make claims that never become true.

You're so presumptuous. I'd already read the first link you sent me and I visited the second  link you sent me because I post in good faith, unlike you.

You spend a third of your posts making presumptions about what I've done.  You spend a third of your posts bragging about the things you've done.  You spend the remaining third of your posts lamenting that the enormous problems in the information technology industry will never be resolved.

You're wrong.  They will be resolved, because fewer and fewer people are prepared to pay for hardware and applications that don't work correctly in the long term.

---

### Post by hereamack on 2021-11-19
How to install your Canon PIXMA iP1700 printer to the Ubuntu 20.04.3 LTS 64 bit operating system so that you are able to print to your Canon PIXMA iP1700 printer from the Ubuntu 20.04.3 LTS 64 bit operating system...


(I am very grateful to Thierry Huchard for his expert assistance in providing this solution to me, without which it would not be possible for me as a new user of Ubuntu to print to my Canon PIXMA iP1700 printer from the Ubuntu 20.04.3 LTS 64 bit operating system.)


1. Connect the power cable that was supplied with your Canon PIXMA iP1700 printer to a power outlet and to your printer.

2. Turn the power outlet on.

3. Connect your printer to your computer via the USB cable that was supplied with your printer.

4. Turn your printer on.

5. Click on the power icon in the top-right corner of the Ubuntu user interface.

6. Click on &#8220;Settings&#8221;, then &#8220;Printers&#8221;, then the green button labelled &#8220;Add&#8230;&#8221; near the top-right corner of the &#8220;Settings&#8221; dialog box.

7. Click on the printer that appears in the &#8220;Add Printer&#8221; dialog box, then click on the green button labelled &#8220;Add&#8221; in the top-right corner of the &#8220;Add Printer&#8221; dialog box.

8. Click on the &#8220;Show Applications&#8221; icon comprising nine small squares in the bottom-left corner of the Ubuntu user interface.

9. Scroll down to the bottom of the applications shown in alphabetical order and click on &#8220;Utilities&#8221;.

10. In the &#8220;Utilities&#8221; dialog box that appears, scroll down to the bottom of the applications shown in alphabetical order and click on &#8220;Terminal&#8221;.

11. Select each of the following six commands one by one and execute them one by one in the &#8220;Terminal&#8221; by clicking the scroll button on your mouse to copy each of the following six commands one by one to the flashing cursor next to the &#8220;$&#8221; symbol in the &#8220;Terminal&#8221; and pressing the "Enter" key on your keyboard to execute them one by one.

(After you execute the first of the following six commands, if this command is the first command that you execute in the &#8220;Terminal&#8221; after logging into to your user account associated with the installation of the Ubuntu operating system on your computer, you will be prompted for the password to this user account in order to authorise the execution of this command.  You will not be prompted for this password in order to authorise the execution of subsequent commands that you execute in the &#8220;Terminal&#8221; during this user session before logging out of this user account, such as by initiating a &#8220;Power Off&#8221; by clicking on the power icon in the top-right corner of the Ubuntu user interface.)

sudo dpkg --add-architecture i386

wget [https://launchpad.net/~thierry-f/+archive/ubuntu/fork-michael-gruz/+files/cnijfilter-ip1900series_4.10+3.5.4-1904ubuntu1_i386.deb](https://launchpad.net/~thierry-f/+archive/ubuntu/fork-michael-gruz/+files/cnijfilter-ip1900series_4.10+3.5.4-1904ubuntu1_i386.deb)

wget [https://launchpad.net/~thierry-f/+archive/ubuntu/fork-michael-gruz/+files/cnijfilter-common_4.10+3.5.4-1904ubuntu1_i386.deb](https://launchpad.net/~thierry-f/+archive/ubuntu/fork-michael-gruz/+files/cnijfilter-common_4.10+3.5.4-1904ubuntu1_i386.deb)

sudo apt update

sudo dpkg -i --force-all ./cnijfilter-ip1900series_4.10+3.5.4-1904ubuntu1_i386.deb ./cnijfilter-common_4.10+3.5.4-1904ubuntu1_i386.deb

sudo apt install -f

system-config-printer


12. Click on the power icon in the top-right corner of the Ubuntu user interface and click on "Settings".

13. Click on "Printers" and then click on the cog-like settings icon associated with the Canon PIXMA iP1700 printer that you have already added.

14. Click on "Printer Details" and then click on "Install PPD File...".

15. Select the PPD file for the Canon PIXMA iP1900 printer using the following path:

Other Locations / Computer / usr / share / ppd / canonip1900.ppd

16. Click on "Open" in the top-right corner of the user interface.

17. Close the "Printer Details" dialog box.


If you're like me, you should now be able to print to your Canon PIXMA iP1700 printer from the Ubuntu 20.04.3 LTS 64 bit operating system.

---

### Post by hereamack on 2021-11-19
I'm glad that's over.

---

