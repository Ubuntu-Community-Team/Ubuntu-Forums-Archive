---
title: "Problem scanning multiple pages from flatbed with Brother MCF-6490CW"
date: 2009-12-11
forum: Hardware
---

### Post by LucaBri on 2009-12-11
Dear All,
   I am relatively new to Ubuntu and Linux in general.
I recently purchased a Brother all-in-one MCF-6490CW because I needed a large flatbed surface for scanning books.
I was able to install the driver and scan with XSane, gscan2pdf and via the command 'scanimage' but I am absolutely unable to batch scan multiple pages from the flatbed.
After the first page scanned successfully I invariably get an error saying that there is no paper **in the ADF** (Automatic Document Feeder) even if the parameter I set clearly define "Flatbed"  as the source.
Here is what I get when I use scanimage:

scanimage -b --source 'FlatBed' --batch-count=3  --mode "True Gray" --resolution 300
WARNING: Unhandled message: interface=org.freedesktop.DBus.Introspectable, path=/, member=Introspect
scanimage: rounded value of br-x from 297 to 296.973
scanimage: rounded value of br-y from 420 to 419.962
Scanning 3 pages, incrementing by 1, numbering from 1
Scanning page 1
Scanned page 1. (scanner status = 5)
Scanning page 2
scanimage: sane_start: Document feeder out of documents

As I said, the first (and only) page get scanned correctly.
Also, I receive the WARNING message with every scan command I issue (not just batch) and the scanner takes about 20 seconds to get started.

Please note that I had an 8 years old HP 6110x all in one and I could scan multiple pages from the flatbed without any problem (but the flatbed was too small for my purposes).

Also, I am able to scan multiple pages from the flatbed in Windows XP with FineReader 9 (but I don't want to)

Please help! :(

Thanks

Luca

---

