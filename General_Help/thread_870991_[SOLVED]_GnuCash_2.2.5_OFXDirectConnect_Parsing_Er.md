---
title: "[SOLVED] GnuCash 2.2.5 OFXDirectConnect Parsing Error OFX"
date: 2008-07-26
forum: General Help
---

### Post by tgerbert on 2008-07-26
I've finally managed to get GnuCash 2.2.5 compiled with OFX and HBCI support, and I've run through the Aq Banking Wizard successfully (the wizard will connect and download the list of accounts)

However, when I try and perform an online action in GnuCash an OFX parsing error results; I set AQOFX_COMM_LOG and re-tried the operation, the results are below (I've deliberately removed USERID and USERPASS, they appear correctly in the actual log file).  Notice that APPID and ACCTID appear to contain invalid characters.

System is Ubuntu Studio 8.04



Sending:
-------------------------------------
OFXHEADER:100

DATA:OFXSGML

VERSION:102

SECURITY:NONE

ENCODING:USASCII

CHARSET:1252

COMPRESSION:NONE

OLDFILEUID:NONE

NEWFILEUID:20080726115246.000



<OFX>

<SIGNONMSGSRQV1>

<SONRQ>

<DTCLIENT>20080726115246.000

<USERID>********

<USERPASS>****

<LANGUAGE>ENG

<FI>

<ORG>USAA

<FID>24591

</FI>

<APPID>hošhoš€oš`=™

<APPVER>1

</SONRQ>

</SIGNONMSGSRQV1>

<BANKMSGSRQV1>

<STMTTRNRQ>

<TRNUID>20080726115246.000

<CLTCOOKIE>1

<STMTRQ>

<BANKACCTFROM>

<BANKID>

<ACCTID>žCš

</BANKACCTFROM>

<INCTRAN>

<DTSTART>19691231

<INCLUDE>Y

</INCTRAN>

</STMTRQ>

</STMTTRNRQ>

</BANKMSGSRQV1>

</OFX>



Received:
-------------------------------------
OFXAdapter: Failed to parse request: Unable to parse a union field "OFXRequest.OFXRequest.SignOnMsgsRqUn": union is empty.
Remaining unparsed data:
<SIGNONMSGSRQV1>

<SONRQ>

<DTCLIENT>20080726115246.000

<USERID>********

<USERPASS>****

<LANGUAGE>ENG

<FI>

<ORG>USAA

<FID>24591

</FI>

<APPID>hošhoš€oš`=™

<APPVER>1

</SONRQ>

</SIGNONMSGSRQV1>

<BANKMSGSRQV1>

<STMTTRNRQ>

<TRNUID>20080726115246.000

<CLTCOOKIE>1

<STMTRQ>

<BANKACCTFROM>

<BANKID>

<ACCTID>žCš

</BANKACCTFROM>

<INCTRAN>

<DTSTART>19691231

<INCLUDE>Y

</INCTRAN>

</STMTRQ>

</STMTTRNRQ>

</BANKMSGSRQV1>

</OFX>

---

### Post by rbmorse on 2008-07-27
Does the financial institution (in this case apparently USAA) support OFX?

---

### Post by tgerbert on 2008-07-27
Yup, although I think the problem is what GnuCash and/or aqbanking is sending in the request (looks like it should be sending the checking account number, but got garbage chars in there instead).

MoneyDance and Microsoft Money didn't have any problems.


Interestingly, I can manually download a .ofx from USAA and it imports correctly in GnuCash (which is my current work-around)

---

### Post by Jive Turkey on 2008-08-03
AFAIK 2.2.5 will not compile with ofxdirectconnect correctly in Hardy due to the Aqbanking version in the repos being not supported.  I'm working on getting 2.2.6 to compile atm, its supposed to support aqbanking 3 now and just came out this week.  I'm struggling with this annoying problem with :
```
 ./configure --enable-aqbanking --enable-ofx
...
checking for SLIB support... configure: error:

   Cannot find SLIB.  Are you sure you have it installed?
   See http://bugzilla.gnome.org/show_bug.cgi?id=347922
   and http://bugzilla.gnome.org/show_bug.cgi?id=483631

```
I've tried w/ both slib-1.6 and 1.8 installed but still no joy, any suggestions?

---

### Post by tgerbert on 2008-08-03
I got 2.2.5 to compile with OFXDirectConnect under Hardy...I just manually installed the appropriate versions of dependant packages, mostly I got them from packages.debian.org.

I had the same issue with SLIB, unfortunately I don't remember exactly how I fixed it...  Try downloading and installing slib from [http://swissnet.ai.mit.edu/~jaffer/SLIB.html](http://swissnet.ai.mit.edu/~jaffer/SLIB.html), then create some sym links

ln -s /usr/share/slib /usr/share/guile/slib
ln -s /usr/share/slib /usr/share/guile/1.6/slib
ln -s /usr/share/slib /usr/share/guile/1.8/slib
ln -s /usr/share/slib /usr/share/guile/site/slib

---

### Post by rbmorse on 2008-08-03
SLIB 1.6 is the correct version for GnuCash 2.2.5. 

Have you run this:

sudo apt-get build-dep gnucash


from a terminal before trying to run configure?

---

### Post by mfleonhardt on 2008-08-03
For some reason, setting the AQOFX_LOG_COMM var doesn't generate a log file for me, but I do get this in /tmp/gnucash.trace when I try to do a DirectConnect with USAA:

```
* 18:16:57  CRIT <gwenhywfar> io_tls.c: 1142: gnutls_handshake: -24 (Decryption has failed.) [fatal]
* 18:16:57  CRIT <aqofxconnect> provider.c:  789: Error exchanging getStatements-request (-66)
```

Using gnucash v. 2.2.6 on Ubuntu 8.04 Hardy

Matt

---

### Post by tgerbert on 2008-08-04
> **mfleonhardt said:**
> For some reason, setting the AQOFX_LOG_COMM var doesn't generate a log file for me, but I do get this in /tmp/gnucash.trace when I try to do a DirectConnect with USAA:

```
* 18:16:57  CRIT <gwenhywfar> io_tls.c: 1142: gnutls_handshake: -24 (Decryption has failed.) [fatal]
* 18:16:57  CRIT <aqofxconnect> provider.c:  789: Error exchanging getStatements-request (-66)
```

Using gnucash v. 2.2.6 on Ubuntu 8.04 Hardy

Matt
mfleonhardt,

I've found the same to be true for me.

---

### Post by Jive Turkey on 2008-08-04
> **rbmorse said:**
> SLIB 1.6 is the correct version for GnuCash 2.2.5. 

Have you run this:

sudo apt-get build-dep gnucash


from a terminal before trying to run configure?

yes! that worked, It built just fine with v2.2.6 using hardy's packages but I'm getting the parsing error too.

If anyone gets a working package built w/ ofx enabled lets share it with bittorrent aye?

---

### Post by mano the shark on 2008-08-05
The endless joy of getting ofx to work with gnucash.

I've been able to enable ofx support for gnucash 2.2.6 and enter my bank information into the aqbanking wizard.  When I select 'get accounts' it prompts for my password, opens a dialog box and closes without proceeding any further.  Now, I know it is gnucash/aqbanking (ubuntu 8.04) because I can install gnucash under windows and retrieve all account information from my bank.

Does anyone have any ideas what I could change to fix this?  I downloaded the source for gnucash 2.2.6 and included everything I did to this point below.

```

sudo apt-get build-dep gnucash
sudo apt-get libaqbanking20-dev libaqbanking20-plugins-qt

sudo ./configure --enable-hbci (no difference if you use --enable-ofx, etc)
sudo make
sudo make install

```

Why don't they make an install file to enable ofx support similar to install-css.sh for playing dvds?

---

### Post by mano the shark on 2008-08-10
Does anyone know a website that has directions to install ofx support for gnucash? (and current unlike [http://wiki.gnucash.org/wiki/Debian]("http://wiki.gnucash.org/wiki/Debian"))

The wiki says to install aqbanking16-qt-wizard which has been dropped and moved to libaqbanking20-plugins in November 2007.

Or how about a program that supports/has directions for ofx as I see that as the biggest reason to use financial software.

---

### Post by tgerbert on 2008-08-10
> **mano the shark said:**
> Does anyone know a website that has directions to install ofx support for gnucash? (and current unlike [http://wiki.gnucash.org/wiki/Debian]("http://wiki.gnucash.org/wiki/Debian"))

The wiki says to install aqbanking16-qt-wizard which has been dropped and moved to libaqbanking20-plugins in November 2007.

Or how about a program that supports/has directions for ofx as I see that as the biggest reason to use financial software.
I think you can get aqbanking16 from [http://packages.debian.org/](http://packages.debian.org/), and everything else on the wiki page you mentioned should work.

You should be able to find your banks OFX settings at [http://www.ofxhome.com/](http://www.ofxhome.com/)

---

### Post by mfleonhardt on 2008-08-18
just a quick bump to see if anyone's got USAA parsing correctly yet...

Matt

---

### Post by tgerbert on 2008-08-20
I gave up on OFX direct connect... when you manually log into the USAA website there's a link somewhere on the account details page to download account activity, if you choose MS Money format you'll get an OFX file (which GNU cash will correctly import).

I just made a bookmark to the download page...

---

### Post by mano the shark on 2008-08-22
I made the switch from windows to ubuntu and I lost functionality using the same program.  That actually bothers me quite a bit.  I use USAA and all access/privileges are correctly setup on their end to allow me to use ofx.  It is gnucash and only gnucash that is the problem.

---

### Post by tgerbert on 2008-08-22
I think, specifically, the problem is with the GnuCash / AqBanking combination (they must not play nice together).

---

### Post by tgerbert on 2008-10-23
(Short answer is put two zero's in front of your checking/savings account numbers in the AqBanking wizard)

Well, I've finally managed to get OFX direct connect working with GnuCash and USAA.  I've since switched to Fedora, so not sure how much of this is still applicable to Ubuntu...

I downloaded & compiled the sources for gwenhywfar-3.5.1 and aqbanking-3.8.0 from [http://www.aquamaniac.de/](http://www.aquamaniac.de/), and got the rest of the dependencies from my distro (goffice 0.6.5, guile 1.8.5, slib 3b1, qt3 3.3.8b-14, GtkHTML 3.18.3, Perl 5.10.0-34, LibOFX 0.9.0, intltool 0.37.1).

Then compiled GnuCash 2.2.7, run through the AqBanking Wizard; the wizard won't download a list of accounts, but I try "Download Transactions" from GnuCash anyway, and low and behold: a useful error message!  It says I supplied an invalid account number to USAA.

So I get a Microsoft Money .ofx file for my accounts from the USAA web site ([https://www.usaa.com/inet/ent_downloadcenter/StatementDownload?action=INIT&cosa=bank](https://www.usaa.com/inet/ent_downloadcenter/StatementDownload?action=INIT&cosa=bank)), and poke through it - it shows my account numbers as starting with two zero's.  Re-run through the AqBanking Wizard, and put two zero's in front of my checking and savings account numbers and voila!  My credit card number appeared in the ofx file exactly as it does on the card.

---

### Post by tedtlogan on 2008-11-27
I'm coming into this late.  I have gnucash 2.2.7 on f10, and I can't get it working with my usaa account.  I click "get accounts" after supposedly setting it up correctly, and it flashes a screen real quick and then turns it off.

I see you guys got to at least some other parsing part?  What am I doing wrong?

do you have your usaa id for userid/customerid?

do you have bank id as 114094041?  Despite the fact that is not your normal routing #?

is server url [https://service2.usaa.com/ofx/OFXServlet?](https://service2.usaa.com/ofx/OFXServlet?)

---

### Post by tgerbert on 2008-11-28
I used 314074269 for the bank id (I think, anyway, got the routing number off my check)  I couldn't get the download accounts to work at all, just had to add them manually.  For my userid I use my usaa member id (should be an 8 digit number).  Looks like you got the right server URL, settings are here: [http://wiki.gnucash.org/wiki/OFX_Direct_Connect_Bank_Settings](http://wiki.gnucash.org/wiki/OFX_Direct_Connect_Bank_Settings)

> **tedtlogan said:**
> I'm coming into this late.  I have gnucash 2.2.7 on f10, and I can't get it working with my usaa account.  I click "get accounts" after supposedly setting it up correctly, and it flashes a screen real quick and then turns it off.

I see you guys got to at least some other parsing part?  What am I doing wrong?

do you have your usaa id for userid/customerid?

do you have bank id as 114094041?  Despite the fact that is not your normal routing #?

is server url [https://service2.usaa.com/ofx/OFXServlet?](https://service2.usaa.com/ofx/OFXServlet?)

---

### Post by tedtlogan on 2008-12-03
I'm trying to make sure we both have the same information:

for username, userid and customerid, have your 8 digit usaa id?

bank settings
u.s.a.
314074269

FID: 24591
ORG: USAA
Broker ID: 5874

supports accounts list download
url: [https://service2.usaa.com/ofx/OFXServlet](https://service2.usaa.com/ofx/OFXServlet) 
then click "get accounts?"

I'm a bit confused as to the topic, as it says "solved?"

For me, as soon as I click get accounts, debug window pops up, a few things are said, and it closes after saying "connecting to bank"

---

### Post by tgerbert on 2008-12-04
I'm using GnuCash 2.2.7.

In "User Name" I have my name (apparently this field isn't used for OFX, it's for your benefit).  I have my 8 digit USAA member ID in both "User Id" and "Customer Id".

I have the same values for Country, Bank Id, FID and ORG - I left Broker Id blank (I don't have any investment accounts though, so I don't know if that matters).

I have the same thing for the Server URL, and I have checked "Supports Account List Download", "Supports Statement Download", and "Force SSLv3"

"APPID", "APPVER" and "Header Version" are all blank.

Clicking "Get Accounts" doesn't work for me either; I went to the "Accounts" tab of the AqBanking Wizard and manually added my accounts.  For my credit card account I used the number as it appears on my card, and for my checking and savings account I had to use two zeros (i.e. "00", not "OO") followed by my account number.

---

### Post by tedtlogan on 2008-12-05
So you had the add the accounts manually.

I did everything now, including accounts.

Sending jobs to the bank(s)
Resolving hostname "service2.usaa.com" ...
IP address is 167.24.111.44
Sending request...
Connecting to bank...
Connected.
Waiting for response...
HTTP-Status: 200 (OK)
Parsing response...
Parsing response
Status for signon request: Signon invalid (Code 15500, severity "ERROR")
The user cannot signon because he or she entered an invalid user ID or password.
Status for transaction statement request: Signon invalid (Code 15500, severity "ERROR")
The user cannot signon because he or she entered an invalid user ID or password.
Postprocessing jobs
Resetting provider queues

---

### Post by tgerbert on 2008-12-05
> **tedtlogan said:**
> So you had the add the accounts manually.
...

Parsing response...
Parsing response
Status for signon request: Signon invalid (Code 15500, severity "ERROR")
The user cannot signon because he or she entered an invalid user ID or password.

...


Use your four digit PIN code for Web access, not your logon password.

---

### Post by tedtlogan on 2008-12-05
Thanks.  But now I get this:O

Sending jobs to the bank(s)
Resolving hostname "service2.usaa.com" ...
IP address is 167.24.111.44
Sending request...
Connecting to bank...
Connected.
Waiting for response...
HTTP-Status: 200 (OK)
Parsing response...
Parsing response
Status for signon request: Success (Code 0, severity "INFO")
The server successfully processed the request.
Status for transaction statement request: Account not found (Code 2003, severity "ERROR")
The specified account number does not correspond to one of the user's accounts.
Postprocessing jobs
Resetting provider queues

---

### Post by tgerbert on 2008-12-05
> **tedtlogan said:**
> Status for transaction statement request: Account not found (Code 2003, severity "ERROR")
The specified account number does not correspond to one of the user's accounts.


Did you put two leading zero's in front of your account number?

---

### Post by tedtlogan on 2008-12-07
Yes sir,

00xxxxxxxx

---

### Post by tgerbert on 2008-12-07
> **tedtlogan said:**
> Yes sir, 00xxxxxxxx

Go to [https://www.usaa.com/inet/ent_downloadcenter/StatementDownload?action=INIT&cosa=bank]("https://www.usaa.com/inet/ent_downloadcenter/StatementDownload?action=INIT&cosa=bank"), you can manually download an OFX file from USAA, use a text editor to open the file and check out what USAA says your account numbers are, then make sure you've got identical account numbers in GnuCash's AqBanking Wizard.

---

### Post by tedtlogan on 2008-12-23
Ah, 

I figured it out.  I had the type as "banking account" and changed it to "checking."

It seems everything works now.  Getting transactions works, too.  I'm just wondering if there's a way to automate everything.

---

### Post by theophile on 2009-07-26
Are any USAA customers still able to use GnuCash to automatically download transactions? I'm no newb and I;ve had this working before, but no matter what I do, I still get error parsing server response when trying to sync. In another thread, someone has indicated USAA only allows Quicken and Money to sync:

[http://ubuntuforums.org/showthread.php?t=1045833](http://ubuntuforums.org/showthread.php?t=1045833)

Does anyone currently have this working?

---

### Post by tgerbert on 2009-07-26
I switched to KMyMoney a little while ago, so I'm not sure about GnuCash - but I am able to download statements with KMyMoney, so it's definitely not limited to Quicken/Money.  And as I seem to recall, the OFX plugin in GnuCash identified itself as either Money or Quicken anyway.  

> **theophile said:**
> Are any USAA customers still able to use GnuCash to automatically download transactions? I'm no newb and I;ve had this working before, but no matter what I do, I still get error parsing server response when trying to sync. In another thread, someone has indicated USAA only allows Quicken and Money to sync:

[http://ubuntuforums.org/showthread.php?t=1045833](http://ubuntuforums.org/showthread.php?t=1045833)

Does anyone currently have this working?

---

### Post by mano the shark on 2009-11-27
Just a quick note that while upgrading to Ubuntu 9.10 I noticed that aqbanking had some packages upgraded.  I gave gnucash another try and got OFX to work with USAA.  I had previously installed aqbanking-tools and I am not sure if this is installed by default with gnucash.  The program versions are listed below and these are from the repositories without compiling.

gnucash 2.2.9
aqbanking-tools 4.1.2-1

---

### Post by theophile on 2009-11-30
Thanks for the observation, mano. A while back I had compiled the dev tree and switched my backend to MySQL. Since there's no going back, I'm installing aqbanking from the repos and I'm going to try compiling the latest gnucash svn against it. Since aqbanking does the work anyway, I would think that would be the key. I'll report back as to the results.

In the mean time, mano, could you post up what settings and values you are using for USAA (except your account number and PIN, obviously). Thanks!

---

### Post by mano the shark on 2009-11-30
For user configuration (USAA)

User Name:  first name (don't think it matters)
user id:  member number
customer id:  member number

country:  USA
bank id:  314074269 (the search feature also retrieves this)

FID:  24591
ORG:  USAA
Broker id:  blank
server url:  [https://service2.usaa.com/ofx/OFXServlet](https://service2.usaa.com/ofx/OFXServlet)

Select:  supports account list download, supports statement download and force sslv3

Click get accounts and it will prompt for you pin and retrieve all accounts

All of the accounts will automatically download, but account configuration uses the 314074269 for the bank code and name.  Everything else is straight forward with IBAN and BIC being blank.

Another thing I noticed is there is a verbose debug message for online banking in the preferences that is nice while getting this working.  I don't think this was there earlier or I missed it.

---

### Post by theophile on 2009-12-02
Fantasic. Thanks! The current repo version of aqbanking seems to have made the difference. All my USAA accounts were detected the first time I tried. This is even better than a year ago when I could use it for deposit accounts but it would not grab transactions form my credit card account.

Yippee!

---

### Post by Gibby13 on 2010-01-27
Here is my current setup.
Ubuntu 9.10 x64

User ID: Member number with 2 zero's at the beginning
Customer ID: Same as above
Country: United States of America
Bank ID: 314074269
FID: 24591
ORD: USAA
Server URL: [https://service2.usaa.com/ofx/OFXServlet](https://service2.usaa.com/ofx/OFXServlet)
Account list and Statement checked.
Force SSLv3 checked.

I select Get Accounts and enter my online pin.
It seems to work however I get nothing under accounts....


Please help.... I was getting network error until I changed my User ID to my member number.

---

### Post by Gibby13 on 2010-01-27
Finally, I got it to do my checking account... How do I get it to do all my accounts?

---

### Post by mano the shark on 2010-01-27
Selecting get accounts should download all accounts that are setup for online access.  It is possible you might have to have USAA enable online access to all of your accounts.  For the member number, I don't know if you need the two zeros or is that what you enter when you call them?

---

### Post by Gibby13 on 2010-01-28
I tried that but it only downloaded my checking account. I have a few loans, a Credit Card, money mark, IRA, Savings and a few other accounts that will not download. However GNUCash does not have the simple stuff, like be able to put in interest rates for credit  cards and loans. So I am off again looking for something else. I prefer web base, so my wife can put her receipts in from her computer.

---

### Post by chrisrodgers on 2011-08-23
This was driving me nuts!  I finally got it!  In short, I made my user  id 8 digits (zero filled in the front).  I also checked the Force SSLv3  check box.

So, several folks kept saying to add two 0's in front of  your account number (user id).  I did that and it did not work.  But  one person mentioned 8 characters.  My USAA number is 7 digits long, so I  added just a single 0 in front of my number and now everything works!  I  got a list of accounts automatically.  I can now get account balance  and transactions.

---

