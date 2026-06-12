---
title: "Ubuntu Server 12.04 Cups not sharing well"
date: 2013-06-25
forum: Hardware
---

### Post by remush on 2013-06-25
Just installed Ubuntu Server 12.04 onto PC.

During installation selected ssh server and cups from options.

Ran
- sudo apt-get update
- sudo apt-get upgrade

No problems so far.

Edited my /etc/cupsd.conf file so that I could use a web gui from windows computer to install and configure attached Samsung ML-2010 printer.

Successfully installed the samsung printer from windows computer via the webgui.

Test print via web gui works fine.

I've installed the printer onto a windows computer using following address
[https://10.1.1.201:631/printers/Samsung_ML-2010](https://10.1.1.201:631/printers/Samsung_ML-2010)

I used the "Samsung Universal Print Driver 2" which i downloaded from samsungs website.

Printer installs onto windows xp pro with no complaints, using above network details and driver.

Running test print from windows to the cups print server, see's nothing printed, however the cups job list shows jobs as completed.

I've attached the samsung printer directly to a windows xp pro computer, and installed with the windows driver, and it prints fine.

Suggestions and comments welcome :)

---

### Post by tgalati4 on 2013-06-25
Look through the log files in /var/log/cups and see if there is anything of interest.  There are access, error, and page logs.  Go through all of them to determine what is going on.  Note the time that you sent the files to the printer.  Each entry has a time stamp.

Post any entries that you don't understand.

You might need to set up a second printer as "RAW" for printing from Windows machines.  But look through the log files first.

---

### Post by remush on 2013-06-25
I've got loglevel set to debug, when it was set to info error_log was very empty.

Heres error_log output for a print test from windows.

D [26/Jun/2013:13:22:05 +1000] cupsdAcceptClient: 17 from 10.1.1.123:631 (IPv4)
D [26/Jun/2013:13:22:05 +1000] Connection from 10.1.1.123 now encrypted.
D [26/Jun/2013:13:22:05 +1000] cupsdReadClient: 17 WAITING Closing on EOF
D [26/Jun/2013:13:22:05 +1000] cupsdCloseClient: 17
D [26/Jun/2013:13:22:05 +1000] SSL shutdown successful!
D [26/Jun/2013:13:22:05 +1000] cupsdSetBusyState: newbusy="Not busy", busy="Not busy"
D [26/Jun/2013:13:22:05 +1000] cupsdReadClient: 17 WAITING Closing on EOF
D [26/Jun/2013:13:22:05 +1000] cupsdCloseClient: 17
D [26/Jun/2013:13:22:05 +1000] cupsdSetBusyState: newbusy="Not busy", busy="Not busy"
D [26/Jun/2013:13:22:05 +1000] cupsdAcceptClient: 17 from 10.1.1.123:631 (IPv4)
D [26/Jun/2013:13:22:05 +1000] Connection from 10.1.1.123 now encrypted.
D [26/Jun/2013:13:22:05 +1000] cupsdReadClient: 17 GET /admin HTTP/1.1
D [26/Jun/2013:13:22:05 +1000] cupsdSetBusyState: newbusy="Active clients", busy="Not busy"
D [26/Jun/2013:13:22:06 +1000] cupsdAuthorize: Authorized as user using Basic
D [26/Jun/2013:13:22:06 +1000] [CGI] argv[0] = "/usr/lib/cups/cgi-bin/admin.cgi"
D [26/Jun/2013:13:22:06 +1000] [CGI] envp[0] = "CUPS_CACHEDIR=/var/cache/cups"
D [26/Jun/2013:13:22:06 +1000] [CGI] envp[1] = "CUPS_DATADIR=/usr/share/cups"
D [26/Jun/2013:13:22:06 +1000] [CGI] envp[2] = "CUPS_DOCROOT=/usr/share/cups/doc-root"
D [26/Jun/2013:13:22:06 +1000] [CGI] envp[3] = "CUPS_FONTPATH=/usr/share/cups/fonts"
D [26/Jun/2013:13:22:06 +1000] [CGI] envp[4] = "CUPS_REQUESTROOT=/var/spool/cups"
D [26/Jun/2013:13:22:06 +1000] [CGI] envp[5] = "CUPS_SERVERBIN=/usr/lib/cups"
D [26/Jun/2013:13:22:06 +1000] [CGI] envp[6] = "CUPS_SERVERROOT=/etc/cups"
D [26/Jun/2013:13:22:06 +1000] [CGI] envp[7] = "CUPS_STATEDIR=/var/run/cups"
D [26/Jun/2013:13:22:06 +1000] [CGI] envp[8] = "HOME=/var/spool/cups/tmp"
D [26/Jun/2013:13:22:06 +1000] [CGI] envp[9] = "PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [26/Jun/2013:13:22:06 +1000] [CGI] envp[10] = "SERVER_ADMIN=stephenbh@hotmail.com"
D [26/Jun/2013:13:22:06 +1000] [CGI] envp[11] = "SOFTWARE=CUPS/1.5.3"
D [26/Jun/2013:13:22:06 +1000] [CGI] envp[12] = "TMPDIR=/var/spool/cups/tmp"
D [26/Jun/2013:13:22:06 +1000] [CGI] envp[13] = "USER=root"
D [26/Jun/2013:13:22:06 +1000] [CGI] envp[14] = "CUPS_SERVER=/var/run/cups/cups.sock"
D [26/Jun/2013:13:22:06 +1000] [CGI] envp[15] = "CUPS_ENCRYPTION=IfRequested"
D [26/Jun/2013:13:22:06 +1000] [CGI] envp[16] = "IPP_PORT=631"
D [26/Jun/2013:13:22:06 +1000] [CGI] envp[17] = "AUTH_TYPE=Basic"
D [26/Jun/2013:13:22:06 +1000] [CGI] envp[18] = "LANG=en_US.UTF8"
D [26/Jun/2013:13:22:06 +1000] [CGI] envp[19] = "REDIRECT_STATUS=1"
D [26/Jun/2013:13:22:06 +1000] [CGI] envp[20] = "GATEWAY_INTERFACE=CGI/1.1"
D [26/Jun/2013:13:22:06 +1000] [CGI] envp[21] = "SERVER_NAME=10.1.1.201"
D [26/Jun/2013:13:22:06 +1000] [CGI] envp[22] = "SERVER_PORT=631"
D [26/Jun/2013:13:22:06 +1000] [CGI] envp[23] = "REMOTE_ADDR=10.1.1.123"
D [26/Jun/2013:13:22:06 +1000] [CGI] envp[24] = "REMOTE_HOST=10.1.1.123"
D [26/Jun/2013:13:22:06 +1000] [CGI] envp[25] = "SCRIPT_NAME=/admin"
D [26/Jun/2013:13:22:06 +1000] [CGI] envp[26] = "SCRIPT_FILENAME=/usr/share/cups/doc-root/admin"
D [26/Jun/2013:13:22:06 +1000] [CGI] envp[27] = "REMOTE_USER=user"
D [26/Jun/2013:13:22:06 +1000] [CGI] envp[28] = "SERVER_PROTOCOL=HTTP/1.1"
D [26/Jun/2013:13:22:06 +1000] [CGI] envp[29] = "HTTP_COOKIE=org.cups.sid=1e17c219c178c2f2eb2a595bded99f21"
D [26/Jun/2013:13:22:06 +1000] [CGI] envp[30] = "HTTP_USER_AGENT=Mozilla/5.0 (Windows NT 5.1) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/27.0.1453.116 Safari/537.36"
D [26/Jun/2013:13:22:06 +1000] [CGI] envp[31] = "HTTP_REFERER=https://10.1.1.201:631/printers/Samsung_ML-2010"
D [26/Jun/2013:13:22:06 +1000] [CGI] envp[32] = "REQUEST_METHOD=GET"
D [26/Jun/2013:13:22:06 +1000] [CGI] envp[33] = "QUERY_STRING="
D [26/Jun/2013:13:22:06 +1000] [CGI] envp[34] = "HTTPS=ON"
D [26/Jun/2013:13:22:06 +1000] [CGI] Started /usr/lib/cups/cgi-bin/admin.cgi (PID 2008)
I [26/Jun/2013:13:22:06 +1000] Started "/usr/lib/cups/cgi-bin/admin.cgi" (pid=2008)
D [26/Jun/2013:13:22:06 +1000] cupsdSendCommand: 17 file=18
D [26/Jun/2013:13:22:06 +1000] [CGI] admin.cgi started...
D [26/Jun/2013:13:22:06 +1000] cupsdAcceptClient: 19 from localhost (Domain)
D [26/Jun/2013:13:22:06 +1000] [CGI] http=0x21a899e8
D [26/Jun/2013:13:22:06 +1000] [CGI] cgiSetVariable: SECTION="admin"
D [26/Jun/2013:13:22:06 +1000] [CGI] cgiSetVariable: REFRESH_PAGE=""
D [26/Jun/2013:13:22:06 +1000] [CGI] org.cups.sid cookie is "1e17c219c178c2f2eb2a595bded99f21"
D [26/Jun/2013:13:22:06 +1000] [CGI] No form data, showing main menu...
D [26/Jun/2013:13:22:06 +1000] [CGI] cgiSetVariable: DEBUG_LOGGING="CHECKED"
D [26/Jun/2013:13:22:06 +1000] [CGI] cgiSetVariable: REMOTE_ADMIN="CHECKED"
D [26/Jun/2013:13:22:06 +1000] [CGI] cgiSetVariable: SHARE_PRINTERS="CHECKED"
D [26/Jun/2013:13:22:06 +1000] [CGI] cgiSetVariable: USER_CANCEL_ANY="CHECKED"
D [26/Jun/2013:13:22:06 +1000] [CGI] cgiSetVariable: HAVE_GSSAPI="1"
D [26/Jun/2013:13:22:06 +1000] [CGI] cgiSetVariable: KERBEROS=""
D [26/Jun/2013:13:22:06 +1000] [CGI] cgiSetVariable: HAVE_DNSSD="1"
D [26/Jun/2013:13:22:06 +1000] [CGI] cgiSetVariable: HAVE_LDAP="1"
D [26/Jun/2013:13:22:06 +1000] [CGI] cgiSetVariable: HAVE_LIBSLP="1"
D [26/Jun/2013:13:22:06 +1000] [CGI] cgiSetVariable: BROWSE_LOCAL_CUPS="CHECKED"
D [26/Jun/2013:13:22:06 +1000] [CGI] cgiSetVariable: BROWSE_LOCAL_DNSSD="CHECKED"
D [26/Jun/2013:13:22:06 +1000] [CGI] cgiSetVariable: PRESERVE_JOB_HISTORY="CHECKED"
D [26/Jun/2013:13:22:06 +1000] [CGI] cgiSetVariable: MAX_CLIENTS="100"
D [26/Jun/2013:13:22:06 +1000] [CGI] cgiSetVariable: MAX_JOBS="500"
D [26/Jun/2013:13:22:06 +1000] [CGI] cgiSetVariable: MAX_LOG_SIZE="0"
D [26/Jun/2013:13:22:06 +1000] [CGI] /usr/share/cups/drivers/pscript5.dll: No such file or directory
D [26/Jun/2013:13:22:06 +1000] cupsdReadClient: 19 POST / HTTP/1.1
D [26/Jun/2013:13:22:06 +1000] cupsdSetBusyState: newbusy="Active clients", busy="Active clients"
D [26/Jun/2013:13:22:06 +1000] cupsdAuthorize: No authentication data provided.
D [26/Jun/2013:13:22:06 +1000] cupsdReadClient: 19 1.1 Get-Subscriptions 1
D [26/Jun/2013:13:22:06 +1000] Get-Subscriptions ipp://localhost/
D [26/Jun/2013:13:22:06 +1000] Get-Subscriptions client-error-not-found: No subscriptions found.
D [26/Jun/2013:13:22:06 +1000] Returning IPP client-error-not-found for Get-Subscriptions (ipp://localhost/) from localhost
D [26/Jun/2013:13:22:06 +1000] cupsdSetBusyState: newbusy="Active clients", busy="Active clients"
D [26/Jun/2013:13:22:06 +1000] [CGI] cgiSetVariable: SERVER_NAME="10.1.1.201"
D [26/Jun/2013:13:22:06 +1000] [CGI] cgiSetVariable: REMOTE_USER="user"
D [26/Jun/2013:13:22:06 +1000] [CGI] cgiSetVariable: CUPS_VERSION="CUPS v1.5.3"
D [26/Jun/2013:13:22:06 +1000] [CGI] cgiSetVariable: TITLE="Administration"
D [26/Jun/2013:13:22:06 +1000] [CGI] cgiSetVariable: SERVER_NAME="10.1.1.201"
D [26/Jun/2013:13:22:06 +1000] [CGI] cgiSetVariable: REMOTE_USER="user"
D [26/Jun/2013:13:22:06 +1000] [CGI] cgiSetVariable: CUPS_VERSION="CUPS v1.5.3"
D [26/Jun/2013:13:22:06 +1000] Script header: Content-Type: text/html;charset=utf-8
D [26/Jun/2013:13:22:06 +1000] Script header: 
D [26/Jun/2013:13:22:06 +1000] cupsdReadClient: 19 WAITING Closing on EOF
D [26/Jun/2013:13:22:06 +1000] cupsdCloseClient: 19
D [26/Jun/2013:13:22:06 +1000] cupsdSetBusyState: newbusy="Active clients", busy="Active clients"
D [26/Jun/2013:13:22:06 +1000] PID 2008 (/usr/lib/cups/cgi-bin/admin.cgi) exited with no errors.
D [26/Jun/2013:13:22:06 +1000] cupsdSetBusyState: newbusy="Not busy", busy="Active clients"
D [26/Jun/2013:13:22:07 +1000] cupsdReadClient: 17 GET /admin/log/error_log? HTTP/1.1
D [26/Jun/2013:13:22:07 +1000] cupsdSetBusyState: newbusy="Active clients", busy="Not busy"
D [26/Jun/2013:13:22:07 +1000] cupsdAuthorize: Authorized as user using Basic


Heres some output from access_log
10.1.1.123 - user [26/Jun/2013:13:22:07 +1000] "GET /admin/log/error_log? HTTP/1.1" 200 348529 - -

Output from page_log
Samsung_ML-2010 Adra Training 15 [26/Jun/2013:13:19:42 +1000] 2 1 - 10.1.1.123 Test Page - -


It might be worth noting that when print from windows, the printer attached to the ubuntu server actually starts to make some noise, but it does not print a page.

---

