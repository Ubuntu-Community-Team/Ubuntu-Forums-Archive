---
title: "Thunderbird Addressbook as Data Source for Open Office"
date: 2008-09-18
forum: General Help
---

### Post by zerubbabel on 2008-09-18
This question has been asked several times in archived threads, but with no satisfactory answer, but I did get a clear answer on the OpenOffice forum: The Ubuntu customized version of OpenOffice 2.4.1 does not provide access to the Thunderbird addressbook as a data source for mail merges, since Evolution is the default mail client. So one must install the generic OpenOffice distribution in order to use TB as a data source. Considering the popularity of Thunderbird, it seems unreasonable to omit it as a data source option. I hope this will change in the next release of Ubuntu. I am not willing to switch to Evolution, as I am quite happy with Thunderbird, and I doubt that I am alone in this preference.

So now, if I install the generic OpenOffice distribution on top of my pre-configured OpenOffice, what complications does that present?

---

### Post by zerubbabel on 2008-11-29
Now that OpenOffice 3.0 is out, I wonder if anything is changed about this... Does anyone know how to add the Thunderbird address book as a data source in  OpenOffice 3.0?

---

### Post by tekknokrat on 2008-12-16
Why dont you use a shared address data source like ldap? If its for company use imo its worth a try, also writing support is planned for 3.0 of thunderbird.

---

### Post by TeXtonyx on 2008-12-16
> **zerubbabel said:**
> Now that OpenOffice 3.0 is out, I wonder if anything is changed about this... Does anyone know how to add the Thunderbird address book as a data source in  OpenOffice 3.0?

[http://www.linux.com/articles/41283](http://www.linux.com/articles/41283)

This article is 4 years old, but I tend to think it will still be
much the same, and it mentions Thunderbird. I recently exported
my address book from Thunderbird and then imported it into Eudora,
the new one from SourceForge which is much like Thunderbird.

I exported from Thunderbird as LDIF, which is text based.
[http://www.zytrax.com/books/ldap/ch8/#format-over](http://www.zytrax.com/books/ldap/ch8/#format-over)

This is pretty much a universal format for a database for years.

If you need the OpenOffice standard rather than Ubuntu, (backup)
[http://www.tectonic.co.za/?p=3363](http://www.tectonic.co.za/?p=3363)
I also had javascript enabled.

I don't have OpenOffice installed on this partition so I will
reboot and test that old reference on Edubuntu which comes with
OOo. I've also read that one can share Thunderbird profiles
from one drive to another, Windows and Linux, which I guess takes
care of syncing but I don't like all my eggs in one basket.

---

### Post by TeXtonyx on 2008-12-16
> **zerubbabel said:**
> Now that OpenOffice 3.0 is out, I wonder if anything is changed about this... Does anyone know how to add the Thunderbird address book as a data source in  OpenOffice 3.0?

Yes, but using the OpenOffice version available from OpenOffice, not Ubuntu,
did you mean a workaround or just how to do this in general?

Applications -> Office -> OpenOffice 3.0 Base
File -> Wizards -> Address Data Source --> Thunderbird (7 or 8 options to choose from)

The Help file is the screenshot on left, and the result is the next screenshot.

You could try exporting the Address Book from Thunderbird (.ldif format) and
the using OOo Base -> File - Open and navigate to /Documents or wherever you
saved your TBaddressBook.ldif and select it, and then open it in OOo Base.

Perhaps the Ubuntu version of OOo just tinkered with the GUI and took
it off the menu. But it is more complicated to remove the functionality
of the underlying file structure. I mean that though there may not be a
wizard way, the manual way may still work.

---

