---
title: "[SOLVED] Osmo won’t save Outlook contacts imported via .CSV file"
date: 2008-10-02
forum: General Help
---

### Post by slackgadget on 2008-10-02
I am trying to copy contacts from Outlook 2003 on my XP desktop to my Fujitsu laptop which is running Xubuntu 8.04. I seem to be able to import all my contacts into Osmo okay but as soon as I close the program and re-open, my contacts have disappeared.

On my first attempt, I exported the contents of my Outlook address book without any modifications. Osmo duly recognized the file and was happy to import. What’s more, the contacts stayed saved every time I opened Osmo.

The only problem was, I noticed all the email addresses, web addresses and ‘notes’ sections present in Outlook were not present in my Osmo contacts. I put this down to the fact that Osmo has a max of 52 fields while Outlook has considerably more. These extra Outlook fields just seemed to drop off the edge of the table during the import process.

So, to import **all** my data, I tried selecting ‘map custom fields’ during the Outlook export, making sure I had a maximum of 52 fields or less. During the import, Osmo very politely lets you assign your Outlook fields to corresponding Osmo fields (eg: ‘categories’ becomes ‘group’ and so on) a very neat feature. I used this and imported. Lo and behold, I had successfully (and very easily) imported all my contacts. All data, all necessary fields, everything. Then I closed Osmo and re-opened to discover every single contact had disappeared.

Since then:
[LIST=1]
[*]I have tried opening, editing and re-saving the .CSV file (as opposed to using the ‘map custom fields’ feature in XP – no joy
[*]I have imported edited .CSV files and edited a few of them, saved and closed – they still disappeared.
[*]I have installed different versions of Osmo including .deb versions and tarballs – still no luck.
[*]I have installed Osmo from the command line following instructions given by the following thread: [http://www.ubuntugeek.com/howto-setup-osmo-personal-organizer-in-ubuntu.html](http://www.ubuntugeek.com/howto-setup-osmo-personal-organizer-in-ubuntu.html)
[*]I have also installed following instructions at: [http://ubuntuforums.org/archive/index.php/t-616116.html](http://ubuntuforums.org/archive/index.php/t-616116.html)
[*]I have tried both Osmo-0.2.2 and the latest Osmo-0.2.4
[*]I have made sure the ‘save data after every modification’ box in Osmo’s Options panel is ticked (version 0.2.4) and then modified a few entries.
[*]I have entered a few addresses by hand, saved (they stayed after close) and then imported again. All contacts still disappeared after closedown.
[*]I have also met all dependencies:
[/LIST] 
[LIST]
[*]libxml2
[*]libxml2-dev
[*]libgtk2.0-dev
[*]libgettext-ruby1.8
[*]libc6 
[*]libcairo2 
[*]libglib2.0-0 (>= 2.16.0) 
[*]libgringotts2 
[*]libical0 
[*]libpango1.0-0 (>= 1.20.2)
[/LIST]
I’d love to know if anyone has a workaround for this. Of all the .CSV-compatible addressbooks I’ve seen, this one is the lightest, and best featured (which makes it great for Xfce users like me). I have around 700 contacts to import from Outlook and I’d rather not do them by hand.

Any suggestions would be very welcome.

---

### Post by slackgadget on 2008-10-14
Okay, figured out what’s happening here by running Osmo from the terminal. It seems Osmo has problems with the ampersand (‘&’) symbol in .CSV file imports. If you’re like me, you probably have a few of these little guys spread through your Outlook contacts data, especially in company names and groups (eg: P&O, AT&T, W.H.Smith & Son, Marks & Spencer etc).

Osmo will import your contacts okay, but on reopening, the ampersands in the data throw up errors. Enough errors and Osmo ‘forgets’ your entire contact list.

It’s worth noting that this bug may occur with other, more exotic symbols. If you’re experiencing a similar problem, then check your data.

I’ve reported this as a bug. Hopefully this may get patched upstream. Until then, here’s a workaround for exporting Outlook contacts to Osmo:

1.	In Outlook, go to contacts and select File>Import and Export.
2.	Select ‘Export to a File’ hit ‘Next’.
3.	Select ‘Comma Separated Values (DOS)’ >Next
4.	In the panel ‘Select Folder to Export From’ choose ‘contacts’ from the tree >Next.
5.	Choose somewhere to save the exported file in Windows >Next.
6.	Select ‘Map Custom Fields’. You’ll now see two panels side-by-side. The one on the right shows what will be exported. It’s important to reduce the amount of fields here to 52 or less as this is the maximum amount of fields Osmo seems to be able to import. To do this, simply select a field from the right panel and drag it into the left panel (choose fields you won’t need like carphone, ISDN, billing and account information, for example). Windows will remember this mapping next time you export your contacts, which can be useful for regular updates.
7.	Hit ‘Okay’.
8.	Click ‘Finish’ and Outlook with export to a .CSV file.
9.	Next, open the CSV file with Excel.
10.	Select Edit>Replace (or hit Cntl+H).
11.	Find what - &
12.	Replace with – and
13.	Hit ‘Replace All’. Excel will now replace all ampersands with ‘and’.
14.	Save the file. You may get an error that reads ‘.CSV may contain features that are not compatible with .CSV (comma delimited).’ Just select ‘yes’ and close.
Now, transfer this .CSV file to your Linux box and open Osmo.
15.	Go to contacts and select ‘Import Contacts’. Select the location of the file. Hit ‘Okay’.
16.	An ‘Import Contacts’ window will now appear. Check that the box ‘Use first record as header’ is unchecked.
17.	From the drop-down menus listed next to ‘field type’, select the Osmo field that corresponds most closely to the Outlook fields listed next to ‘Value:’ (for example, select ‘Group’ for ‘Categories’, ‘Additional info’ for ‘Notes’, ‘Organization’ for ‘Company’, etc).
18.	Hit ‘Import’.
Osmo should now import all your Outlook data into corresponding fields and your data should stay saved.

---

### Post by slackgadget on 2008-10-22
This bug will be fixed soon. It seems the ampersand issue is caused by Osmo not importing groups correctly (or 'categories' in Outlook parlance).

So, an even quicker workaround is simply to open your exported .CSV file in Excel, select the 'Categories' column and remove all the ampersands. (You may still have to reduce your fields down to 52, though).

---

