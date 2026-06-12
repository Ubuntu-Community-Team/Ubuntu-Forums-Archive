---
title: "MultiUser Quickbooks - Local and Remote"
date: 2008-10-26
forum: General Help
---

### Post by xphlo on 2008-10-26
I am currently setting up a server for a small business. 
The company does its computer work using quickbooks, word docs, and spreadsheets (all clients are windows flavors). The server was to provide file and print sharing on the LAN, and remote access to the filesystem for selected users. The game plan was to use debian, and all was well.

Today, they contacted me about adding remote quickbooks access to the setup. After 2 hours of google, i have a handful of options, but im not sure which implementation is going to work out the best. Quickbooks needs to be in multiuser mode during the business hours, but in the evening, remote access in single user mode is desired.

The server was originally going to use samba for local file/print share, and vsftpd for remote access. My server was not going to mess with quickbooks at all. They could store backups to it or something, but no real support for hosting the quickbooks files.

Also, I dont think the Linux Database Server Management is an option. My clients use all Quickbooks Pro, and an upgrade to Enterprise is not currently an option.

My options as far as I know...

1. Switch to Windows - 
While not ideal, I can still manage samba and an ftp server with ease. The only reason to go with this option is so I can install Quickbooks on the server, and set it up to host to the rest of the clients.

2. Quickbooks Alternate Multi-User Setup - 
This is a multi-user setup described [here.]("http://support.quickbooks.intuit.com/support/Pages/InProductHelp/Core/QB2K6/admin_n/multiuser_n/task_multiuser_setup_non.html"). I get the host computer (the boss's computer lets say) to map a special samba share just for the quickbooks data. All clients on the LAN will go through the boss. But for remote access, I point the ftp to the QB directory, and it will be that users responsibility to push and pull files on the server as needed.

3. Tell them I wont do it - 
It would be great if I can help them, but I dont want a rigged solution that is prone to breaking (such as assuming responsible use with an FTP protocol described in option #2). If they know they will want Quickbooks at home tonight, either copy the files onto a disk, or make a copy in the FTP dir and don't alter the originals directly.

Im looking for some experience. Is there a better option I didn't cover? If not, which option have/would you gone/go with?

Thanks much.

---

### Post by ahoffman on 2009-02-24
Hello,

I was wondering if you were ever able to resolve your problem. If, what kind of configuration are you using? It sounds like you have an similar environment. We are running QB Pro on all the client machines so therefore do not have the Linux Database Manager but do use Samba running on Ubuntu. We been running into problems where the company file locks for one individual user preventing other users on the network to open the file. I was just curious if you may have experience this same problem. If you could let me know it would be greatly appreciated.

Thanks,
Aaron

---

