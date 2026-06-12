---
title: "Install MSOffice (W95) in 8.04 error"
date: 2009-03-02
forum: Installation &amp; Upgrades
---

### Post by col48 on 2009-03-02
I've been told it should be possible to install MSOffice (Windows95 version) in Ubuntu 8.04.  Specifically I want to use Access to edit some complex databases.

So I follow the guide in the thread about installing Office2003 as best I can - this seems to be the nearest approximation....  But this is what I get:  All this is running as root.

I have added blank lines to separate what i did from the response.

root@richard-desktop:/home/richard/download# wine richedit30.exe

fixme:setupapi:SetupDefaultQueueCallbackW notification 262144 params 32f980,0
err:setupapi:SetupDefaultQueueCallbackW copy error 0 L"C:\\windows\\temp\\IXP000.TMP\\riched20.dll" -> L"C:\\windows\\system32\\riched20.dll"
fixme:setupapi:SetupDefaultQueueCallbackW notification 262144 params 32f980,0
err:setupapi:SetupDefaultQueueCallbackW copy error 0 L"C:\\windows\\temp\\IXP000.TMP\\riched32.dll" -> L"C:\\windows\\system32\\riched32.dll"

root@richard-desktop:/home/richard/download# wine msiexec /i msxml3.msi

fixme:advapi:LookupAccountNameW (null) L"root" (nil) 0x32f7fc (nil) 0x32f800 0x32f7f4 - stub
fixme:advapi:LookupAccountNameW (null) L"root" 0x12ebb8 0x32f7fc 0x14da80 0x32f800 0x32f7f4 - stub
fixme:msi:msi_unimplemented_action_stub MigrateFeatureStates -> 2 ignored L"Upgrade" table values
fixme:msi:ControlEvent_SpawnWaitDialog Doing Nothing
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"SetODBCFolders"
fixme:msi:msi_unimplemented_action_stub MigrateFeatureStates -> 2 ignored L"Upgrade" table values
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:msi_unimplemented_action_stub RemoveExistingProducts -> 2 ignored L"Upgrade" table values

root@richard-desktop:/home/richard/download# winecfg

root@richard-desktop:/home/richard/download# cd /cdrom

root@richard-desktop:/cdrom# wine setup.exe

fixme:ntdll:server_ioctl_file Unsupported ioctl 24000 (device=2 access=1 func=0 method=0)
fixme:odbc:SQLConfigDataSource (nil) 1304 "" #0104
wine: Unhandled page fault on read access to 0x0000000a at address 0x7b853eeb (thread 0009), starting debugger...
fixme:ntdll:server_ioctl_file Unsupported ioctl 24000 (device=2 access=1 func=0 method=0)
fixme:odbc:SQLConfigDataSource (nil) 1304 "" #0104
wine: Unhandled page fault on read access to 0x0000000a at address 0x7b853eeb (thread 0009), starting debugger...

and it hits the buffers with a message box about ODBC's SQLRemoveDriver (if I have remembered it right).

What do I need to do?

---

### Post by Mark Phelps on 2009-03-02
Basically, you can NOT install MS Office directly in Ubuntu.  

You can install a virtualization product in Ubuntu (i.e., virtualbox, VM Ware), install MS Windows into that, and install Windows apps into that virtual OS).

There is also an environment known as Wine that will allow you to install SOME MS applications inside it, but you have to install Wine first.  

Before you do that, would advise that you go to the Codeweavers website and check out their database of Wine compatible MS apps.  Don't know personally if Access is supported.

---

### Post by sehrgut on 2009-03-02
Dude, did you even *read* his report? He's using WINE.

To the OP, sorry, I've little experience getting WINE to run non-trivial apps. My only question would be, is this a vanilla WINE install? If not, remember WINE has all the cruft of a normal Windoze box, and I'd try installing it on a fresh install of WINE.

---

### Post by Mark Phelps on 2009-03-03
Sorry, missed that ... Anyway, link below is to the CodeWeavers compatibility pages, where is shows only SOME Access versions will work with Wine. 

If you will bother to read this, you will notice that it says that Access 2003 is "known not to work".

[=ASC;company_curPos=1250;company_id=1"]http://www.codeweavers.com/compatibility/browse/company/?company_sort[company_name]=ASC;company_curPos=1250;company_id=1]("http://www.codeweavers.com/compatibility/browse/company/?company_sort[company_name)

---

### Post by maybeway36 on 2009-03-03
Are you using Office '95 (a.k.a. Access 7.0)? That probably installs differently (more simply) than Office 2003.

---

### Post by col48 on 2009-03-04
I'm using Office95 - at least that's what made the databases.  Would it install under Wine?  If so, how?

I have tried inserting the Office95 CD (the autorun then tries to run and fails due to lack of permissions) then in Terminal (as me not as root)
cd /media/cdrom
wine setup.exe

It then thinks for a bit and starts the install process, getting not very far (as far as being happy with the product key and telling me it will install into c:/MSOffice) before it quits with an error box titled "Error while configuring ODBC Drivers" which says "ODBC's SQLRemoveDriver failed for Microsoft Access Driver (*.mdb)"

Meanwhile the Terminal output is saying
fixme: odbc:SQLConfigDataSource (nil) 1296 "" #0104
wine: Unhandled page fault on read access to 0x0000000a at address 0x7b853c5b (thread 0009), starting debugger...

Thanks for the link to codeweavers... it looks like they don't look back beyond Windows97 and for Access only at Access2000.  I can manage without Access95 but it would be useful occasionally.  I exported the databases to spreadsheets in Windows95 so can load them into OpenOffice base but it is not yet as powerful.

---

