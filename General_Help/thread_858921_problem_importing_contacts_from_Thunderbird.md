---
title: "problem importing contacts from Thunderbird"
date: 2008-07-14
forum: General Help
---

### Post by jakub12 on 2008-07-14
I followed the Evolution user guide to import Outlook contacts via Thunderbird. It works as per instructions until I get to the point where in the "Import single file" dialog box I select the file "Inbox" (containing my contacts presumably) and click Open. The import wizard doesn't than highlight the "Forward" button so obviously I can't continue.
I also noticed that when I launch the Import Wizard it doesn't give me the option to select automatic file type. All the file types in the dropbox are grayed out and there isn't an automatic file type option anywhere.
Please help!!!

Thanks,
Jakub

---

### Post by jakub12 on 2008-07-15
I solved the problem by installing Plaxo as sugested in one of the threads on this forum, and syncing my Outlook Contacts in Windows, than Rebooting in Ubuntu, exporting as vCards.
The vCard format was recognized by Evolution and that solved the problem. My 2007 Outlook-Thunderbird-Evolution path didn't work though for some reason.
Jakub

---

### Post by pmorton on 2008-07-29
> **jakub12 said:**
> I followed the Evolution user guide to import Outlook contacts via Thunderbird. It works as per instructions until I get to the point where in the "Import single file" dialog box I select the file "Inbox" (containing my contacts presumably) and click Open. The import wizard doesn't than highlight the "Forward" button so obviously I can't continue.
I also noticed that when I launch the Import Wizard it doesn't give me the option to select automatic file type. All the file types in the dropbox are grayed out and there isn't an automatic file type option anywhere.
Please help!!!

Thanks,
Jakub


This is a problem, requiring just the kind of guddle of a workaround you describe. What's astonishing really is the lack of information on evolution's  addressbook  .db file structure.

I tried as many of the methods of exporting from Thunderbird and importing into Evolution as I could find, but they all gave me jumbled fields that would take as long to fix  as re-entering the data.

However, a method  that worked for me was to install the Thunderbird add-on  morefunctionsforAB-0.5.2.2.xpi (get from [http://nic-nac-project.de/~kaosmos/morecols-en.html](http://nic-nac-project.de/~kaosmos/morecols-en.html)). Then right click on the Thunderbird address book you want to export and select the option "Export as vcf". That creates  a single .vcf file that you can then import with the built-in Evolution import function. It gave me a near perfect field mapping.

---

