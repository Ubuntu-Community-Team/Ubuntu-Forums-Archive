---
title: "Awardspace error 500"
date: 2008-08-13
forum: General Help
---

### Post by Jdm111 on 2008-08-13
Hi. I have made my site with kompoZer and it uploaded it to awardspace with gftp which went fine. But when i try to load it i get this...
" [sherwoodfc.awardspace.co.uk] [Wed Aug 13 21:39:40 2008] [error] [client 79.68.190.146] Premature end of script headers: index.html, referer: [http://cp8.awardspace.com/subdomain_manager.html](http://cp8.awardspace.com/subdomain_manager.html)
Error 500: Script Execution Failure
Description: The server encountered an internal error or misconfiguration and was unable to complete your request.

Most common reasons for returning this error message are:

• File Upload Mode
When you upload Perl, CGI scripts via FTP you should use always ASCII mode. If you get "Error 500: Script Execution Failure" you should check whether your FTP client uses ASCII mode when uploading your scripts, because if it uses BINARY mode to upload your scripts they won't work on the server. The problem caused by wrong upload mode is associated with the way different operating systems handle the "end of line" character. Unix system uses a "line-feed" (LF), Windows uses a "carriage-return" (CR) and "line-feed" (LF) pair. That's why it is very important that you set the uploading mode to ASCII.

• File Permissions
When you upload scripts via FTP the file permissions are set by default to 755. If you get "Error 500: Script Execution Failure" you should check whether your scripts have 755 permissions. Otherwise your scripts have lower level of permissions and does not support execution upon request. The octal representation of the 755 permission is equal to the following textual format: -rwxr-xr-x
Most FTP clients support the CHMOD command which is used for setting file permissions. In case you have set improper permissions to your scripts, use your FTP client and set "Read, Write, Execute" permissions for the owner, "Read, Execute" permissions for the group and everyone else.

• Script Errors
This is the third well known reason for getting "Error 500: Script Execution Failure" upon execution of your scripts. Check your scripts for any obvious syntax or programming errors to make sure your code is not broken.


Remember: When you get a "Error 500: Script Execution Failure", you should always check for any file uploading problems (ASCII/BINARY) and the executable permission settings. Once those are checked and verified, it looks like there is a syntax error or some other problem in the script. "

---

