---
title: "I don't understand this performance difference...."
date: 2011-05-30
forum: Hardware
---

### Post by rodrigogp on 2011-05-30
Hi,

Hope you can help me to clarify my doubts! :)

I'm running a process with grails to load info from a spreadsheet into a data base.

My local machine has 4GB RAM and iCore7 1.73GHZ processor
The server machine has 2GB RAM and a Intel E7400 2.8GHZ Dual Core

Both with a 500GB hard drive

Below you can see the time in seconds to load different information from the spread sheet into the DB.


SERVER UBUNTU 9.04 64BIT

LOAD DICTIONARY TABLES STARTING...
LOAD DICTIONARY TABLES : TOTAL Processing time = 5.31
2011-05-30 11:49:39,210 [main] DEBUG dataImport.CatalogueDataLoader  - LOADING CATALOGUE...

2011-05-30 11:49:39,582 [main] DEBUG dataImport.CatalogueDataLoader  - CATALOGUE LOAD : TOTAL Processing time 0.371 


LOCAL UBUNTU 10.10 64BIT

LOAD DICTIONARY TABLES STARTING...
LOAD DICTIONARY TABLES : TOTAL Processing time = 32.641
2011-05-30 12:36:38,875 [main] DEBUG dataImport.CatalogueDataLoader  - LOADING CATALOGUE...

2011-05-30 12:36:40,214 [main] DEBUG dataImport.CatalogueDataLoader  - CATALOGUE LOAD : TOTAL Processing time 1.338 



The CATALOGUE LOAD : TOTAL is just for 1 line of the spreadsheet but I have to load around 7K lines, so the time difference is important. In my machine is taking more than 1 hour and in the server is just 10min. It does not make sense I think.


Can someone explain this?

Thanks!

---

