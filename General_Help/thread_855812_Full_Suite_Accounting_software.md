---
title: "Full Suite Accounting software"
date: 2008-07-10
forum: General Help
---

### Post by infecticide on 2008-07-10
Hello everybody!

I have the need for a full featured accounting suite for a manufacturing business.

The accounting software needs to meet or exceed the features available in [QuickBooks Premier 2008 for manufacturers & wholesalers.](http://quickbooks.intuit.ca/accounting-software/products/industry.jsp?menuLevel=114800005&skuId=B07S07W307001&prodId=114800005&location=1&catId=1&src=ppc&ve=sen&se=google&cmp=Small_Business_EN_Branded&ad=Premier_Manufacturing&kw=QuickBooks_manufacturing)

Also we are using [Number Cruncher: All Order](http://www.numbercruncher.com/solutions/allorder.asp) for inventory control.

Number Cruncher: All Orders references information in Quickbooks, I need something that does the same thing.

I want the whole thing to be database based as currently Quickbooks and All Orders are not, and the amount of data in these apps has ground them to a halt.

Thanks for any leads you might have!

---

### Post by Taxman415a on 2008-07-10
The most unfortunate thing is that all the data is locked up in Intuit's proprietary formats. Which of course they do on purpose.

I'm not sure if what you want is out there, but these links are a good start: [http://www.aaxnet.com/design/linuxacct.html](http://www.aaxnet.com/design/linuxacct.html)
[http://www.linuxjournal.com/content/accounting-software-geek-ranch](http://www.linuxjournal.com/content/accounting-software-geek-ranch)

You'll have to research if any of those meet your needs. Unfortunately last I heard is there weren't great alternatives forcing most people to keep a Windows box around for Quickbooks, or you could run it in a virtual machine on linux. Hopefully if you're exceeding Quickbook's capabilities and need to shell out some cash anyway, the situation is different.

---

### Post by infecticide on 2008-07-11
The issue really is that the Quickbooks and NumberCruncher data files are being accessed via a SMB connection and the sheer size and access method (streaming the file instead of returning just a result) has become a problem.   Since these apps aren't designed to be used in this fasion, I'm looking for something that can be used with a database, since I believe this to be a much more efficient method.

---

### Post by Taxman415a on 2008-07-12
Maybe the virtual machine scenario would solve that problem. Also in doing some searching I did see some of the linux solutions claimed to be heavy duty accounting packages and several claimed to be able to import quickbooks files, so you may have some luck.

---

### Post by infecticide on 2008-07-12
I've seen many packages who could import Quicken files, but haven't seen any for Quickbooks.  Could you provide some names for the packages that import Quickbooks?

---

### Post by techstop on 2008-07-12
If you're after an enterprise-grade open-source accounting package, can I recommend [SQL Ledger]("http://sql-ledger.org/"). I use it for my small business, and it's probably overkill, but it covers your requirements such as;

[LIST]
[*]Invoices, Purchase Orders, Sales Orders, Packing Slips etc
[*]Inventory Control
[*]Job Tracking
[*]Project Tracking
[*]True Multi-user
[*]Customer Reports and Histories
[*]Recurring Transactions
[*]Import / Export / Exchange Rates
[/LIST]

etc...

The project itself is quite active with constant updates, however there is a bit of controversy. 

It forked to become LedgerSMB after a significant dispute regarding some unpatched security issues. The "owner" of the SQL Ledger project had a bit of a turn and attempted to change the licence away from Open Source, but this was soon reversed.

SQL Ledger continues to lack any free documentation, although you can get some help from the SourceForge mailing list. I personally find it disappointing that an open source project is so "secretive", but I have been able to figure out enough about it to make it work for me, and it does a good job. One day I might transfer my accounts to LedgerSMB as they are far more "open" about their project.

You can read a bit about it here;

[http://lwn.net/Articles/227151/](http://lwn.net/Articles/227151/)

Hope this helps. :)

---

### Post by Taxman415a on 2008-07-12
> **infecticide said:**
> I've seen many packages who could import Quicken files, but haven't seen any for Quickbooks.  Could you provide some names for the packages that import Quickbooks?

It took me a bit to find where I read that, but both of these claim to be able to. But you'd have to see if the result is any less of a locked-in proprietary file format than quickbooks. Or maybe quickbooks can export to something more open too.

[http://linuxappfinder.com/package/sureinvoice](http://linuxappfinder.com/package/sureinvoice)
[http://linuxappfinder.com/package/mybooks](http://linuxappfinder.com/package/mybooks)

---

