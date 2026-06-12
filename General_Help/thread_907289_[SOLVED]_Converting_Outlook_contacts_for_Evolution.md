---
title: "[SOLVED] Converting Outlook contacts for Evolution"
date: 2008-09-01
forum: General Help
---

### Post by ^^rac on 2008-09-01
Hi guys!

I have found this somewhere:

To Import Contacts:
First, you will need to use Outlook to export all of your contact to a .csv file. To do this: 

Click on File --> Import and Export.... 
Choose "Export to a file" and click [Next]. 
For the file type choose "Comma Separated Values (DOS)". 
Click [Next]. 
For the folder to export choose "Contacts". 
Name the exported file contacts.csv (no quotation marks) and place it somewhere you can get to it from Linux. 
Click [Next]. 
Click [Finish]. 
From your Linux system, you will then need to convert contacts.csv into files that Evolution can understand by you running it through the Perl script csv2vcard.pl. The program is normally installed with Evolution, but if you don't have it, you can download it from the bottom of this page. Put it in your home directory and make the it executable by running the command:
chmod +x ~/csv2vcard.pl 

Then, run the script to convert your contacts.csv to contacts.vcf. Use the command:
csv2vcard.pl contacts.csv contacts.vcf

Note: If you did not have csv2vcard installed with Evolution, and downloaded it instead, the command will be ./csv2vcard contacts.csv contacts.vcf 

Once you have contacts.vcf, you can import it into Evolution: 

Run Evolution 
Click File --> Import. 
Click [Next]. 
Click on "Import from a single file" 
Click [Next] again. 
For file type choose "VCard...". 
Click [Browse] and select your file. 
Click [Next] then [Import]. 


*The question is, is this the only way to do it.....
*and if so, how do i know if i have the pearl script installed?

Thanks alot!

---

### Post by igknighted on 2008-10-24
Anyone have any idea how to keep contacts synced (automatically) between Outlook and Evolution?  I've got all my contacts in Outlook at the moment, but would like them in Evolution as well.  Both are important, as I don't want to have to keep going back and forth for email, but Outlook must stay up to date with contacts because it syncs to my WM6 phone.

---

