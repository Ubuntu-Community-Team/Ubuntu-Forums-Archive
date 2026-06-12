---
title: "[SOLVED] gFTP suddenly won't connect; neither will Firezilla"
date: 2008-10-05
forum: General Help
---

### Post by Teasdale on 2008-10-05
I've had great luck with gFTP for months and months.

Suddenly today it won't connect to my ISP Host. It connects to my comcast website, but not to my other ISP Host.

ISP Host has been back and forth with me about it via Live Chat and tech support; they recommended coreFTP (a Windows program) and they keep saying, "But it's working for us, we're able to connect to your site via shell to FTP, and coreFTP. This is not an issue with FTP on the server."

But with my gFTP, it tries to connect with passive mode, and then hangs at the "LIST" command. Then gFTP locks up. Firezilla just gives up at that point and says "can't connect."

Yet I have no problem connecting with my comcast site. And, until today, I had no problem connecting to my ISP Host.

Here's the dialog from Firezilla:

Status:	Resolving IP-Address for ftp.xxxx.org
Status:	Connecting to 74.xx.xxx.xxx:21...
Status:	Connection established, waiting for welcome message...
Response:	220---------- Welcome to Pure-FTPd [TLS] ----------
Response:	220-You are user number 1 of 50 allowed.
Response:	220-Local time is now 22:51. Server port: 21.
Response:	220-This is a private system - No anonymous login
Response:	220-IPv6 connections are also welcome on this server.
Response:	220 You will be disconnected after 15 minutes of inactivity.
Command:	USER xxxx
Response:	331 User xxxx OK. Password required
Command:	PASS *************
Response:	230-User xxxx has group access to:  xxxx
Response:	230 OK. Current restricted directory is /
Command:	SYST
Response:	215 UNIX Type: L8
Command:	FEAT
Response:	211-Extensions supported:
Response:	 EPRT
Response:	 IDLE
Response:	 MDTM
Response:	 SIZE
Response:	 REST STREAM
Response:	 MLST 
type*;size*;sizd*;modify*;UNIX.mode*;UNIX.uid*;UNIX.gid*;unique*;
Response:	 MLSD
Response:	 ESTP
Response:	 PASV
Response:	 EPSV
Response:	 SPSV
Response:	 ESTA
Response:	 AUTH TLS
Response:	 PBSZ
Response:	 PROT
Response:	211 End.
Status:	Connected
Status:	Retrieving directory listing...
Command:	PWD
Response:	257 "/" is your current location
Command:	TYPE I
Response:	200 TYPE is now 8-bit binary
Command:	PASV
Response:	227 Entering Passive Mode (74,52,239,204,133,24)
Command:	LIST
Error:	Connection timed out
Error:	Failed to retrieve directory listing

---

### Post by Teasdale on 2008-10-05
After going around and around with my ISP Host all day yesterday and them saying "we don't see any problem, it works for us," I got an email this morning saying that they had finally been able to try it with Linux/gFTP, and it was working for them. And now it seems to be working for me, too. I don't know if they fixed something, or whether it was a glitch that worked its way out of the system.

---

