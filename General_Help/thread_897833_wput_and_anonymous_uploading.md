---
title: "wput and anonymous uploading"
date: 2008-08-22
forum: General Help
---

### Post by whiteghetto on 2008-08-22
I am attempting to automate the uploading of the same file repeatedly.
I can upload and overwrite from a windows computer running filezilla 3.111
I cannot upload using wput on Ubuntu 8.04
all 3 machines are on the same LAN

any help or ideas would be greatly appreciated

I cannot upload to the same server and directory with wput
Here is the session from filezilla
```
Response:	220 Welcome to blah FTP service.
Command:	USER anonymous
Response:	331 Please specify the password.
Command:	PASS **************
Response:	230 Login successful.
Status:	Connected
Status:	Starting upload of C:\Users\John\Documents\14meg.file
Command:	CWD /upload
Response:	250 Directory successfully changed.
Command:	TYPE I
Response:	200 Switching to Binary mode.
Command:	PASV
Response:	227 Entering Passive Mode (192,168,25,130,197,81)
Command:	STOR 14meg.file
Response:	150 Ok to send data.
Response:	226 File receive OK.
Status:	File transfer successful
Status:	Starting upload of C:\Users\John\Documents\14meg.file
Status:	Retrieving directory listing...
Command:	PASV
Response:	227 Entering Passive Mode (192,168,25,130,43,69)
Command:	LIST
Response:	150 Here comes the directory listing.
Response:	226 Directory send OK.
Command:	PASV
Response:	227 Entering Passive Mode (192,168,25,130,114,47)
Command:	STOR 14meg.file
Response:	150 Ok to send data.
Response:	226 File receive OK.
Status:	File transfer successful
```

Here is the verbose output from wput

```
lab@lab-01:~$ wput --verbose --reupload 14meg.file ftp://192.168.25.130/upload
--11:01:04-- `14meg.file'
    => ftp://anonymous:xxxxx@192.168.25.130:21/upload
Connecting to 192.168.25.130:21... connected!
==> AUTH TLS ... failed (Please login with USER and PASS.).

Logging in as anonymous ... Logged in!
==> SIZE upload ... failed.
==> TYPE I ... done.
==> PASV ... done.
==> STOR upload ... Send Failed. Skipping this file
FINISHED --11:01:04--
Transmission of 1 file failed.


```

edit
added --reupload command with same results

---

