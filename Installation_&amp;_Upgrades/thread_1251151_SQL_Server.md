---
title: "SQL Server"
date: 2009-08-27
forum: Installation &amp; Upgrades
---

### Post by oceanfirehawk on 2009-08-27
So I tried to install SQL Ledger and got the following:

```
jacob@jacob-laptop:~$ sudo apt-get install sql-ledger
[sudo] password for jacob: 
Sorry, try again.
[sudo] password for jacob: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.28-11 linux-headers-2.6.28-11-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  apache2 apache2-mpm-worker apache2-utils apache2.2-common libapr1
  libaprutil1 libdbd-pg-perl libdbi-perl libnet-daemon-perl libplrpc-perl
Suggested packages:
  apache2-doc apache2-suexec apache2-suexec-custom dbishell
  texlive-latex-extra tetex-extra postgresql
The following NEW packages will be installed:
  apache2 apache2-mpm-worker apache2-utils apache2.2-common libapr1
  libaprutil1 libdbd-pg-perl libdbi-perl libnet-daemon-perl libplrpc-perl
  sql-ledger
0 upgraded, 11 newly installed, 0 to remove and 28 not upgraded.
Need to get 5838kB of archives.
After this operation, 45.6MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com jaunty-updates/main libapr1 1.2.12-5ubuntu0.1 [109kB]
Get:2 http://us.archive.ubuntu.com jaunty-updates/main libaprutil1 1.2.12+dfsg-8ubuntu0.3 [72.6kB]
Get:3 http://us.archive.ubuntu.com jaunty-updates/main apache2-utils 2.2.11-2ubuntu2.3 [150kB]
Get:4 http://us.archive.ubuntu.com jaunty-updates/main apache2.2-common 2.2.11-2ubuntu2.3 [784kB]
Get:5 http://us.archive.ubuntu.com jaunty-updates/main apache2-mpm-worker 2.2.11-2ubuntu2.3 [245kB]
Get:6 http://us.archive.ubuntu.com jaunty-updates/main apache2 2.2.11-2ubuntu2.3 [46.4kB]
Get:7 http://us.archive.ubuntu.com jaunty/main libnet-daemon-perl 0.43-1 [46.9kB]
Get:8 http://us.archive.ubuntu.com jaunty/main libplrpc-perl 0.2020-1 [36.0kB]
Get:9 http://us.archive.ubuntu.com jaunty/main libdbi-perl 1.607-1 [791kB]
Get:10 http://us.archive.ubuntu.com jaunty/universe libdbd-pg-perl 2.11.7-1 [203kB]
Get:11 http://us.archive.ubuntu.com jaunty/universe sql-ledger 2.8.18-1 [3355kB]
Fetched 5838kB in 33s (174kB/s)                                                
Selecting previously deselected package libapr1.
(Reading database ... 140958 files and directories currently installed.)
Unpacking libapr1 (from .../libapr1_1.2.12-5ubuntu0.1_i386.deb) ...
Selecting previously deselected package libaprutil1.
Unpacking libaprutil1 (from .../libaprutil1_1.2.12+dfsg-8ubuntu0.3_i386.deb) ...
Selecting previously deselected package apache2-utils.
Unpacking apache2-utils (from .../apache2-utils_2.2.11-2ubuntu2.3_i386.deb) ...
Selecting previously deselected package apache2.2-common.
Unpacking apache2.2-common (from .../apache2.2-common_2.2.11-2ubuntu2.3_i386.deb) ...
Selecting previously deselected package apache2-mpm-worker.
Unpacking apache2-mpm-worker (from .../apache2-mpm-worker_2.2.11-2ubuntu2.3_i386.deb) ...
Selecting previously deselected package apache2.
Unpacking apache2 (from .../apache2_2.2.11-2ubuntu2.3_all.deb) ...
Selecting previously deselected package libnet-daemon-perl.
Unpacking libnet-daemon-perl (from .../libnet-daemon-perl_0.43-1_all.deb) ...
Selecting previously deselected package libplrpc-perl.
Unpacking libplrpc-perl (from .../libplrpc-perl_0.2020-1_all.deb) ...
Selecting previously deselected package libdbi-perl.
Unpacking libdbi-perl (from .../libdbi-perl_1.607-1_i386.deb) ...
Selecting previously deselected package libdbd-pg-perl.
Unpacking libdbd-pg-perl (from .../libdbd-pg-perl_2.11.7-1_i386.deb) ...
Selecting previously deselected package sql-ledger.
Unpacking sql-ledger (from .../sql-ledger_2.8.18-1_all.deb) ...
Processing triggers for man-db ...
Processing triggers for ufw ...
Setting up libapr1 (1.2.12-5ubuntu0.1) ...

Setting up libaprutil1 (1.2.12+dfsg-8ubuntu0.3) ...

Setting up apache2-utils (2.2.11-2ubuntu2.3) ...
Setting up apache2.2-common (2.2.11-2ubuntu2.3) ...
Enabling site default.
Enabling module alias.
Enabling module autoindex.
Enabling module dir.
Enabling module env.
Enabling module mime.
Enabling module negotiation.
Enabling module setenvif.
Enabling module status.
Enabling module auth_basic.
Enabling module deflate.
Enabling module authz_default.
Enabling module authz_user.
Enabling module authz_groupfile.
Enabling module authn_file.
Enabling module authz_host.

Setting up apache2-mpm-worker (2.2.11-2ubuntu2.3) ...
 * Starting web server apache2                                                  apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
                                                                         [ OK ]

Setting up apache2 (2.2.11-2ubuntu2.3) ...
Setting up libnet-daemon-perl (0.43-1) ...
Setting up libplrpc-perl (0.2020-1) ...
Setting up libdbi-perl (1.607-1) ...
Setting up libdbd-pg-perl (2.11.7-1) ...
Setting up sql-ledger (2.8.18-1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
jacob@jacob-laptop:~$ 

```

Is it installed now? If so, how do I launch the program. I don't see it anywhere in the "applications" drop down. 

Thanks,

Jake

---

### Post by unutbu on 2009-08-27
Run ```
dpkg --listfiles sql-ledger
```
to list the files the sql-ledger package has installed. (It looks like it installed successfully).

Usually the executable is located in a directory with "bin" in its name.

---

### Post by oceanfirehawk on 2009-08-27
> **unutbu said:**
> Run ```
dpkg --listfiles sql-ledger
```
to list the files the sql-ledger package has installed. (It looks like it installed successfully).

Usually the executable is located in a directory with "bin" in its name.

I got:

```
/var/lib/sql-ledger/templates/Traditional_Chinese_Big5-credit_invoice.html
/var/lib/sql-ledger/templates/Traditional_Chinese_Big5-credit_note.html
/var/lib/sql-ledger/templates/Traditional_Chinese_Big5-debit_invoice.html
/var/lib/sql-ledger/templates/Traditional_Chinese_Big5-debit_note.html
/var/lib/sql-ledger/templates/Traditional_Chinese_Big5-income_statement.html
/var/lib/sql-ledger/templates/Traditional_Chinese_Big5-invoice.html
/var/lib/sql-ledger/templates/Traditional_Chinese_Big5-letterhead.html
/var/lib/sql-ledger/templates/Traditional_Chinese_Big5-packing_list.html
/var/lib/sql-ledger/templates/Traditional_Chinese_Big5-pick_list.html
/var/lib/sql-ledger/templates/Traditional_Chinese_Big5-purchase_order.html
/var/lib/sql-ledger/templates/Traditional_Chinese_Big5-remittance_voucher.html
/var/lib/sql-ledger/templates/Traditional_Chinese_Big5-request_quotation.html
/var/lib/sql-ledger/templates/Traditional_Chinese_Big5-sales_order.html
/var/lib/sql-ledger/templates/Traditional_Chinese_Big5-sales_quotation.html
/var/lib/sql-ledger/templates/Traditional_Chinese_Big5-statement.html
/var/lib/sql-ledger/templates/Traditional_Chinese_Big5-timecard.html
/var/lib/sql-ledger/templates/Traditional_Chinese_Big5-work_order.html
/var/lib/sql-ledger/templates/Traditional_Chinese_UTF8-ap_transaction.html
/var/lib/sql-ledger/templates/Traditional_Chinese_UTF8-ar_transaction.html
/var/lib/sql-ledger/templates/Traditional_Chinese_UTF8-balance_sheet.html
/var/lib/sql-ledger/templates/Traditional_Chinese_UTF8-bin_list.html
/var/lib/sql-ledger/templates/Traditional_Chinese_UTF8-credit_invoice.html
/var/lib/sql-ledger/templates/Traditional_Chinese_UTF8-credit_note.html
/var/lib/sql-ledger/templates/Traditional_Chinese_UTF8-debit_invoice.html
/var/lib/sql-ledger/templates/Traditional_Chinese_UTF8-debit_note.html
/var/lib/sql-ledger/templates/Traditional_Chinese_UTF8-income_statement.html
/var/lib/sql-ledger/templates/Traditional_Chinese_UTF8-invoice.html
/var/lib/sql-ledger/templates/Traditional_Chinese_UTF8-letterhead.html
/var/lib/sql-ledger/templates/Traditional_Chinese_UTF8-packing_list.html
/var/lib/sql-ledger/templates/Traditional_Chinese_UTF8-pick_list.html
/var/lib/sql-ledger/templates/Traditional_Chinese_UTF8-purchase_order.html
/var/lib/sql-ledger/templates/Traditional_Chinese_UTF8-remittance_voucher.html
/var/lib/sql-ledger/templates/Traditional_Chinese_UTF8-request_quotation.html
/var/lib/sql-ledger/templates/Traditional_Chinese_UTF8-sales_order.html
/var/lib/sql-ledger/templates/Traditional_Chinese_UTF8-sales_quotation.html
/var/lib/sql-ledger/templates/Traditional_Chinese_UTF8-statement.html
/var/lib/sql-ledger/templates/Traditional_Chinese_UTF8-timecard.html
/var/lib/sql-ledger/templates/Traditional_Chinese_UTF8-work_order.html
/var/lib/sql-ledger/templates/Brazilian_Portuguese-ap_transaction.tex
/var/lib/sql-ledger/templates/Brazilian_Portuguese-ar_transaction.tex
/var/lib/sql-ledger/templates/Brazilian_Portuguese-bin_list.tex
/var/lib/sql-ledger/templates/Brazilian_Portuguese-check.tex
/var/lib/sql-ledger/templates/Brazilian_Portuguese-credit_invoice.tex
/var/lib/sql-ledger/templates/Brazilian_Portuguese-credit_note.tex
/var/lib/sql-ledger/templates/Brazilian_Portuguese-debit_invoice.tex
/var/lib/sql-ledger/templates/Brazilian_Portuguese-debit_note.tex
/var/lib/sql-ledger/templates/Brazilian_Portuguese-invoice.tex
/var/lib/sql-ledger/templates/Brazilian_Portuguese-packing_list.tex
/var/lib/sql-ledger/templates/Brazilian_Portuguese-pick_list.tex
/var/lib/sql-ledger/templates/Brazilian_Portuguese-purchase_order.tex
/var/lib/sql-ledger/templates/Brazilian_Portuguese-receipt.tex
/var/lib/sql-ledger/templates/Brazilian_Portuguese-remittance_voucher.tex
/var/lib/sql-ledger/templates/Brazilian_Portuguese-request_quotation.tex
/var/lib/sql-ledger/templates/Brazilian_Portuguese-sales_order.tex
/var/lib/sql-ledger/templates/Brazilian_Portuguese-sales_quotation.tex
/var/lib/sql-ledger/templates/Brazilian_Portuguese-statement.tex
/var/lib/sql-ledger/templates/Brazilian_Portuguese-timecard.tex
/var/lib/sql-ledger/templates/Brazilian_Portuguese-vendor_invoice.tex
/var/lib/sql-ledger/templates/Brazilian_Portuguese-work_order.tex
/var/lib/sql-ledger/templates/Danish-ap_transaction.tex
/var/lib/sql-ledger/templates/Danish-ar_transaction.tex
/var/lib/sql-ledger/templates/Danish-bin_list.tex
/var/lib/sql-ledger/templates/Danish-check.tex
/var/lib/sql-ledger/templates/Danish-credit_invoice.tex
/var/lib/sql-ledger/templates/Danish-credit_note.tex
/var/lib/sql-ledger/templates/Danish-debit_invoice.tex
/var/lib/sql-ledger/templates/Danish-debit_note.tex
/var/lib/sql-ledger/templates/Danish-invoice.tex
/var/lib/sql-ledger/templates/Danish-packing_list.tex
/var/lib/sql-ledger/templates/Danish-pick_list.tex
/var/lib/sql-ledger/templates/Danish-purchase_order.tex
/var/lib/sql-ledger/templates/Danish-receipt.tex
/var/lib/sql-ledger/templates/Danish-remittance_voucher.tex
/var/lib/sql-ledger/templates/Danish-request_quotation.tex
/var/lib/sql-ledger/templates/Danish-sales_order.tex
/var/lib/sql-ledger/templates/Danish-sales_quotation.tex
/var/lib/sql-ledger/templates/Danish-statement.tex
/var/lib/sql-ledger/templates/Danish-timecard.tex
/var/lib/sql-ledger/templates/Danish-vendor_invoice.tex
/var/lib/sql-ledger/templates/Danish-work_order.tex
/var/lib/sql-ledger/templates/Default-ap_transaction.tex
/var/lib/sql-ledger/templates/Default-ar_transaction.tex
/var/lib/sql-ledger/templates/Default-bin_list.tex
/var/lib/sql-ledger/templates/Default-check.tex
/var/lib/sql-ledger/templates/Default-credit_invoice.tex
/var/lib/sql-ledger/templates/Default-credit_note.tex
/var/lib/sql-ledger/templates/Default-debit_invoice.tex
/var/lib/sql-ledger/templates/Default-debit_note.tex
/var/lib/sql-ledger/templates/Default-invoice.tex
/var/lib/sql-ledger/templates/Default-letterhead.tex
/var/lib/sql-ledger/templates/Default-packing_list.tex
/var/lib/sql-ledger/templates/Default-pick_list.tex
/var/lib/sql-ledger/templates/Default-purchase_order.tex
/var/lib/sql-ledger/templates/Default-receipt.tex
/var/lib/sql-ledger/templates/Default-remittance_voucher.tex
/var/lib/sql-ledger/templates/Default-request_quotation.tex
/var/lib/sql-ledger/templates/Default-sales_order.tex
/var/lib/sql-ledger/templates/Default-sales_quotation.tex
/var/lib/sql-ledger/templates/Default-statement.tex
/var/lib/sql-ledger/templates/Default-timecard.tex
/var/lib/sql-ledger/templates/Default-vendor_invoice.tex
/var/lib/sql-ledger/templates/Default-work_order.tex
/var/lib/sql-ledger/templates/Dutch-ap_transaction.tex
/var/lib/sql-ledger/templates/Dutch-ar_transaction.tex
/var/lib/sql-ledger/templates/Dutch-bin_list.tex
/var/lib/sql-ledger/templates/Dutch-check.tex
/var/lib/sql-ledger/templates/Dutch-credit_invoice.tex
/var/lib/sql-ledger/templates/Dutch-credit_note.tex
/var/lib/sql-ledger/templates/Dutch-debit_invoice.tex
/var/lib/sql-ledger/templates/Dutch-debit_note.tex
/var/lib/sql-ledger/templates/Dutch-invoice.tex
/var/lib/sql-ledger/templates/Dutch-packing_list.tex
/var/lib/sql-ledger/templates/Dutch-pick_list.tex
/var/lib/sql-ledger/templates/Dutch-purchase_order.tex
/var/lib/sql-ledger/templates/Dutch-receipt.tex
/var/lib/sql-ledger/templates/Dutch-remittance_voucher.tex
/var/lib/sql-ledger/templates/Dutch-request_quotation.tex
/var/lib/sql-ledger/templates/Dutch-sales_order.tex
/var/lib/sql-ledger/templates/Dutch-sales_quotation.tex
/var/lib/sql-ledger/templates/Dutch-statement.tex
/var/lib/sql-ledger/templates/Dutch-timecard.tex
/var/lib/sql-ledger/templates/Dutch-vendor_invoice.tex
/var/lib/sql-ledger/templates/Dutch-work_order.tex
/var/lib/sql-ledger/templates/Estonian-ap_transaction.tex
/var/lib/sql-ledger/templates/Estonian-ar_transaction.tex
/var/lib/sql-ledger/templates/Estonian-bin_list.tex
/var/lib/sql-ledger/templates/Estonian-check.tex
/var/lib/sql-ledger/templates/Estonian-credit_invoice.tex
/var/lib/sql-ledger/templates/Estonian-credit_note.tex
/var/lib/sql-ledger/templates/Estonian-debit_invoice.tex
/var/lib/sql-ledger/templates/Estonian-debit_note.tex
/var/lib/sql-ledger/templates/Estonian-invoice.tex
/var/lib/sql-ledger/templates/Estonian-letterhead.tex
/var/lib/sql-ledger/templates/Estonian-packing_list.tex
/var/lib/sql-ledger/templates/Estonian-pick_list.tex
/var/lib/sql-ledger/templates/Estonian-purchase_order.tex
/var/lib/sql-ledger/templates/Estonian-receipt.tex
/var/lib/sql-ledger/templates/Estonian-remittance_voucher.tex
/var/lib/sql-ledger/templates/Estonian-request_quotation.tex
/var/lib/sql-ledger/templates/Estonian-sales_order.tex
/var/lib/sql-ledger/templates/Estonian-sales_quotation.tex
/var/lib/sql-ledger/templates/Estonian-statement.tex
/var/lib/sql-ledger/templates/Estonian-timecard.tex
/var/lib/sql-ledger/templates/Estonian-vendor_invoice.tex
/var/lib/sql-ledger/templates/Estonian-work_order.tex
/var/lib/sql-ledger/templates/Estonian_UTF8-ap_transaction.tex
/var/lib/sql-ledger/templates/Estonian_UTF8-ar_transaction.tex
/var/lib/sql-ledger/templates/Estonian_UTF8-bin_list.tex
/var/lib/sql-ledger/templates/Estonian_UTF8-check.tex
/var/lib/sql-ledger/templates/Estonian_UTF8-credit_invoice.tex
/var/lib/sql-ledger/templates/Estonian_UTF8-credit_note.tex
/var/lib/sql-ledger/templates/Estonian_UTF8-debit_invoice.tex
/var/lib/sql-ledger/templates/Estonian_UTF8-debit_note.tex
/var/lib/sql-ledger/templates/Estonian_UTF8-invoice.tex
/var/lib/sql-ledger/templates/Estonian_UTF8-letterhead.tex
/var/lib/sql-ledger/templates/Estonian_UTF8-packing_list.tex
/var/lib/sql-ledger/templates/Estonian_UTF8-pick_list.tex
/var/lib/sql-ledger/templates/Estonian_UTF8-purchase_order.tex
/var/lib/sql-ledger/templates/Estonian_UTF8-receipt.tex
/var/lib/sql-ledger/templates/Estonian_UTF8-remittance_voucher.tex
/var/lib/sql-ledger/templates/Estonian_UTF8-request_quotation.tex
/var/lib/sql-ledger/templates/Estonian_UTF8-sales_order.tex
/var/lib/sql-ledger/templates/Estonian_UTF8-sales_quotation.tex
/var/lib/sql-ledger/templates/Estonian_UTF8-statement.tex
/var/lib/sql-ledger/templates/Estonian_UTF8-timecard.tex
/var/lib/sql-ledger/templates/Estonian_UTF8-work_order.tex
/var/lib/sql-ledger/templates/French-ap_transaction.tex
/var/lib/sql-ledger/templates/French-ar_transaction.tex
/var/lib/sql-ledger/templates/French-bin_list.tex
/var/lib/sql-ledger/templates/French-check.tex
/var/lib/sql-ledger/templates/French-credit_invoice.tex
/var/lib/sql-ledger/templates/French-credit_note.tex
/var/lib/sql-ledger/templates/French-debit_invoice.tex
/var/lib/sql-ledger/templates/French-debit_note.tex
/var/lib/sql-ledger/templates/French-invoice.tex
/var/lib/sql-ledger/templates/French-packing_list.tex
/var/lib/sql-ledger/templates/French-pick_list.tex
/var/lib/sql-ledger/templates/French-purchase_order.tex
/var/lib/sql-ledger/templates/French-receipt.tex
/var/lib/sql-ledger/templates/French-remittance_voucher.tex
/var/lib/sql-ledger/templates/French-request_quotation.tex
/var/lib/sql-ledger/templates/French-sales_order.tex
/var/lib/sql-ledger/templates/French-sales_quotation.tex
/var/lib/sql-ledger/templates/French-statement.tex
/var/lib/sql-ledger/templates/French-timecard.tex
/var/lib/sql-ledger/templates/French-vendor_invoice.tex
/var/lib/sql-ledger/templates/French-work_order.tex
/var/lib/sql-ledger/templates/German-ap_transaction.tex
/var/lib/sql-ledger/templates/German-ar_transaction.tex
/var/lib/sql-ledger/templates/German-bin_list.tex
/var/lib/sql-ledger/templates/German-check.tex
/var/lib/sql-ledger/templates/German-credit_invoice.tex
/var/lib/sql-ledger/templates/German-credit_note.tex
/var/lib/sql-ledger/templates/German-debit_invoice.tex
/var/lib/sql-ledger/templates/German-debit_note.tex
/var/lib/sql-ledger/templates/German-invoice.tex
/var/lib/sql-ledger/templates/German-packing_list.tex
/var/lib/sql-ledger/templates/German-pick_list.tex
/var/lib/sql-ledger/templates/German-purchase_order.tex
/var/lib/sql-ledger/templates/German-receipt.tex
/var/lib/sql-ledger/templates/German-remittance_voucher.tex
/var/lib/sql-ledger/templates/German-request_quotation.tex
/var/lib/sql-ledger/templates/German-sales_order.tex
/var/lib/sql-ledger/templates/German-sales_quotation.tex
/var/lib/sql-ledger/templates/German-statement.tex
/var/lib/sql-ledger/templates/German-timecard.tex
/var/lib/sql-ledger/templates/German-vendor_invoice.tex
/var/lib/sql-ledger/templates/German-work_order.tex
/var/lib/sql-ledger/templates/Hungarian-ap_transaction.tex
/var/lib/sql-ledger/templates/Hungarian-ar_transaction.tex
/var/lib/sql-ledger/templates/Hungarian-bin_list.tex
/var/lib/sql-ledger/templates/Hungarian-check.tex
/var/lib/sql-ledger/templates/Hungarian-credit_invoice.tex
/var/lib/sql-ledger/templates/Hungarian-credit_note.tex
/var/lib/sql-ledger/templates/Hungarian-debit_invoice.tex
/var/lib/sql-ledger/templates/Hungarian-debit_note.tex
/var/lib/sql-ledger/templates/Hungarian-invoice.tex
/var/lib/sql-ledger/templates/Hungarian-packing_list.tex
/var/lib/sql-ledger/templates/Hungarian-pick_list.tex
/var/lib/sql-ledger/templates/Hungarian-purchase_order.tex
/var/lib/sql-ledger/templates/Hungarian-receipt.tex
/var/lib/sql-ledger/templates/Hungarian-remittance_voucher.tex
/var/lib/sql-ledger/templates/Hungarian-request_quotation.tex
/var/lib/sql-ledger/templates/Hungarian-sales_order.tex
/var/lib/sql-ledger/templates/Hungarian-sales_quotation.tex
/var/lib/sql-ledger/templates/Hungarian-statement.tex
/var/lib/sql-ledger/templates/Hungarian-timecard.tex
/var/lib/sql-ledger/templates/Hungarian-vendor_invoice.tex
/var/lib/sql-ledger/templates/Hungarian-work_order.tex
/var/lib/sql-ledger/templates/Italian-ap_transaction.tex
/var/lib/sql-ledger/templates/Italian-ar_transaction.tex
/var/lib/sql-ledger/templates/Italian-bin_list.tex
/var/lib/sql-ledger/templates/Italian-check.tex
/var/lib/sql-ledger/templates/Italian-credit_invoice.tex
/var/lib/sql-ledger/templates/Italian-credit_note.tex
/var/lib/sql-ledger/templates/Italian-debit_invoice.tex
/var/lib/sql-ledger/templates/Italian-debit_note.tex
/var/lib/sql-ledger/templates/Italian-invoice.tex
/var/lib/sql-ledger/templates/Italian-packing_list.tex
/var/lib/sql-ledger/templates/Italian-pick_list.tex
/var/lib/sql-ledger/templates/Italian-purchase_order.tex
/var/lib/sql-ledger/templates/Italian-receipt.tex
/var/lib/sql-ledger/templates/Italian-remittance_voucher.tex
/var/lib/sql-ledger/templates/Italian-request_quotation.tex
/var/lib/sql-ledger/templates/Italian-sales_order.tex
/var/lib/sql-ledger/templates/Italian-sales_quotation.tex
/var/lib/sql-ledger/templates/Italian-statement.tex
/var/lib/sql-ledger/templates/Italian-timecard.tex
/var/lib/sql-ledger/templates/Italian-vendor_invoice.tex
/var/lib/sql-ledger/templates/Italian-work_order.tex
/var/lib/sql-ledger/templates/Norwegian-ap_transaction.tex
/var/lib/sql-ledger/templates/Norwegian-ar_transaction.tex
/var/lib/sql-ledger/templates/Norwegian-bin_list.tex
/var/lib/sql-ledger/templates/Norwegian-check.tex
/var/lib/sql-ledger/templates/Norwegian-credit_invoice.tex
/var/lib/sql-ledger/templates/Norwegian-credit_note.tex
/var/lib/sql-ledger/templates/Norwegian-debit_invoice.tex
/var/lib/sql-ledger/templates/Norwegian-debit_note.tex
/var/lib/sql-ledger/templates/Norwegian-invoice.tex
/var/lib/sql-ledger/templates/Norwegian-packing_list.tex
/var/lib/sql-ledger/templates/Norwegian-pick_list.tex
/var/lib/sql-ledger/templates/Norwegian-purchase_order.tex
/var/lib/sql-ledger/templates/Norwegian-receipt.tex
/var/lib/sql-ledger/templates/Norwegian-remittance_voucher.tex
/var/lib/sql-ledger/templates/Norwegian-request_quotation.tex
/var/lib/sql-ledger/templates/Norwegian-sales_order.tex
/var/lib/sql-ledger/templates/Norwegian-sales_quotation.tex
/var/lib/sql-ledger/templates/Norwegian-statement.tex
/var/lib/sql-ledger/templates/Norwegian-timecard.tex
/var/lib/sql-ledger/templates/Norwegian-vendor_invoice.tex
/var/lib/sql-ledger/templates/Norwegian-work_order.tex
/var/lib/sql-ledger/templates/Russian-ap_transaction.tex
/var/lib/sql-ledger/templates/Russian-ar_transaction.tex
/var/lib/sql-ledger/templates/Russian-bin_list.tex
/var/lib/sql-ledger/templates/Russian-check.tex
/var/lib/sql-ledger/templates/Russian-credit_invoice.tex
/var/lib/sql-ledger/templates/Russian-credit_note.tex
/var/lib/sql-ledger/templates/Russian-debit_invoice.tex
/var/lib/sql-ledger/templates/Russian-debit_note.tex
/var/lib/sql-ledger/templates/Russian-invoice.tex
/var/lib/sql-ledger/templates/Russian-packing_list.tex
/var/lib/sql-ledger/templates/Russian-pick_list.tex
/var/lib/sql-ledger/templates/Russian-purchase_order.tex
/var/lib/sql-ledger/templates/Russian-receipt.tex
/var/lib/sql-ledger/templates/Russian-remittance_voucher.tex
/var/lib/sql-ledger/templates/Russian-request_quotation.tex
/var/lib/sql-ledger/templates/Russian-sales_order.tex
/var/lib/sql-ledger/templates/Russian-sales_quotation.tex
/var/lib/sql-ledger/templates/Russian-statement.tex
/var/lib/sql-ledger/templates/Russian-timecard.tex
/var/lib/sql-ledger/templates/Russian-vendor_invoice.tex
/var/lib/sql-ledger/templates/Russian-work_order.tex
/var/lib/sql-ledger/templates/Service-ap_transaction.tex
/var/lib/sql-ledger/templates/Service-ar_transaction.tex
/var/lib/sql-ledger/templates/Service-bin_list.tex
/var/lib/sql-ledger/templates/Service-check.tex
/var/lib/sql-ledger/templates/Service-credit_invoice.tex
/var/lib/sql-ledger/templates/Service-credit_note.tex
/var/lib/sql-ledger/templates/Service-debit_invoice.tex
/var/lib/sql-ledger/templates/Service-debit_note.tex
/var/lib/sql-ledger/templates/Service-invoice.tex
/var/lib/sql-ledger/templates/Service-packing_list.tex
/var/lib/sql-ledger/templates/Service-pick_list.tex
/var/lib/sql-ledger/templates/Service-purchase_order.tex
/var/lib/sql-ledger/templates/Service-receipt.tex
/var/lib/sql-ledger/templates/Service-remittance_voucher.tex
/var/lib/sql-ledger/templates/Service-request_quotation.tex
/var/lib/sql-ledger/templates/Service-sales_order.tex
/var/lib/sql-ledger/templates/Service-sales_quotation.tex
/var/lib/sql-ledger/templates/Service-statement.tex
/var/lib/sql-ledger/templates/Service-timecard.tex
/var/lib/sql-ledger/templates/Service-vendor_invoice.tex
/var/lib/sql-ledger/templates/Service-work_order.tex
/var/lib/sql-ledger/templates/Slovak-ap_transaction.tex
/var/lib/sql-ledger/templates/Slovak-ar_transaction.tex
/var/lib/sql-ledger/templates/Slovak-bin_list.tex
/var/lib/sql-ledger/templates/Slovak-check.tex
/var/lib/sql-ledger/templates/Slovak-credit_invoice.tex
/var/lib/sql-ledger/templates/Slovak-credit_note.tex
/var/lib/sql-ledger/templates/Slovak-debit_invoice.tex
/var/lib/sql-ledger/templates/Slovak-debit_note.tex
/var/lib/sql-ledger/templates/Slovak-invoice.tex
/var/lib/sql-ledger/templates/Slovak-letterhead.tex
/var/lib/sql-ledger/templates/Slovak-packing_list.tex
/var/lib/sql-ledger/templates/Slovak-pick_list.tex
/var/lib/sql-ledger/templates/Slovak-purchase_order.tex
/var/lib/sql-ledger/templates/Slovak-receipt.tex
/var/lib/sql-ledger/templates/Slovak-remittance_voucher.tex
/var/lib/sql-ledger/templates/Slovak-request_quotation.tex
/var/lib/sql-ledger/templates/Slovak-sales_order.tex
/var/lib/sql-ledger/templates/Slovak-sales_quotation.tex
/var/lib/sql-ledger/templates/Slovak-statement.tex
/var/lib/sql-ledger/templates/Slovak-timecard.tex
/var/lib/sql-ledger/templates/Slovak-vendor_invoice.tex
/var/lib/sql-ledger/templates/Slovak-work_order.tex
/var/lib/sql-ledger/templates/Spanish_A4-ap_transaction.tex
/var/lib/sql-ledger/templates/Spanish_A4-ar_transaction.tex
/var/lib/sql-ledger/templates/Spanish_A4-bin_list.tex
/var/lib/sql-ledger/templates/Spanish_A4-check.tex
/var/lib/sql-ledger/templates/Spanish_A4-credit_invoice.tex
/var/lib/sql-ledger/templates/Spanish_A4-credit_note.tex
/var/lib/sql-ledger/templates/Spanish_A4-debit_invoice.tex
/var/lib/sql-ledger/templates/Spanish_A4-debit_note.tex
/var/lib/sql-ledger/templates/Spanish_A4-invoice.tex
/var/lib/sql-ledger/templates/Spanish_A4-packing_list.tex
/var/lib/sql-ledger/templates/Spanish_A4-pick_list.tex
/var/lib/sql-ledger/templates/Spanish_A4-purchase_order.tex
/var/lib/sql-ledger/templates/Spanish_A4-receipt.tex
/var/lib/sql-ledger/templates/Spanish_A4-remittance_voucher.tex
/var/lib/sql-ledger/templates/Spanish_A4-request_quotation.tex
/var/lib/sql-ledger/templates/Spanish_A4-sales_order.tex
/var/lib/sql-ledger/templates/Spanish_A4-sales_quotation.tex
/var/lib/sql-ledger/templates/Spanish_A4-statement.tex
/var/lib/sql-ledger/templates/Spanish_A4-timecard.tex
/var/lib/sql-ledger/templates/Spanish_A4-vendor_invoice.tex
/var/lib/sql-ledger/templates/Spanish_A4-work_order.tex
/var/lib/sql-ledger/templates/Spanish_Letter-ap_transaction.tex
/var/lib/sql-ledger/templates/Spanish_Letter-ar_transaction.tex
/var/lib/sql-ledger/templates/Spanish_Letter-bin_list.tex
/var/lib/sql-ledger/templates/Spanish_Letter-check.tex
/var/lib/sql-ledger/templates/Spanish_Letter-credit_invoice.tex
/var/lib/sql-ledger/templates/Spanish_Letter-credit_note.tex
/var/lib/sql-ledger/templates/Spanish_Letter-debit_invoice.tex
/var/lib/sql-ledger/templates/Spanish_Letter-debit_note.tex
/var/lib/sql-ledger/templates/Spanish_Letter-invoice.tex
/var/lib/sql-ledger/templates/Spanish_Letter-packing_list.tex
/var/lib/sql-ledger/templates/Spanish_Letter-pick_list.tex
/var/lib/sql-ledger/templates/Spanish_Letter-purchase_order.tex
/var/lib/sql-ledger/templates/Spanish_Letter-receipt.tex
/var/lib/sql-ledger/templates/Spanish_Letter-remittance_voucher.tex
/var/lib/sql-ledger/templates/Spanish_Letter-request_quotation.tex
/var/lib/sql-ledger/templates/Spanish_Letter-sales_order.tex
/var/lib/sql-ledger/templates/Spanish_Letter-sales_quotation.tex
/var/lib/sql-ledger/templates/Spanish_Letter-statement.tex
/var/lib/sql-ledger/templates/Spanish_Letter-timecard.tex
/var/lib/sql-ledger/templates/Spanish_Letter-vendor_invoice.tex
/var/lib/sql-ledger/templates/Spanish_Letter-work_order.tex
/var/lib/sql-ledger/templates/Swedish-ap_transaction.tex
/var/lib/sql-ledger/templates/Swedish-ar_transaction.tex
/var/lib/sql-ledger/templates/Swedish-bin_list.tex
/var/lib/sql-ledger/templates/Swedish-check.tex
/var/lib/sql-ledger/templates/Swedish-credit_invoice.tex
/var/lib/sql-ledger/templates/Swedish-credit_note.tex
/var/lib/sql-ledger/templates/Swedish-debit_invoice.tex
/var/lib/sql-ledger/templates/Swedish-debit_note.tex
/var/lib/sql-ledger/templates/Swedish-invoice.tex
/var/lib/sql-ledger/templates/Swedish-packing_list.tex
/var/lib/sql-ledger/templates/Swedish-pick_list.tex
/var/lib/sql-ledger/templates/Swedish-purchase_order.tex
/var/lib/sql-ledger/templates/Swedish-receipt.tex
/var/lib/sql-ledger/templates/Swedish-remittance_voucher.tex
/var/lib/sql-ledger/templates/Swedish-request_quotation.tex
/var/lib/sql-ledger/templates/Swedish-sales_order.tex
/var/lib/sql-ledger/templates/Swedish-sales_quotation.tex
/var/lib/sql-ledger/templates/Swedish-statement.tex
/var/lib/sql-ledger/templates/Swedish-timecard.tex
/var/lib/sql-ledger/templates/Swedish-work_order.tex
/var/lib/sql-ledger/templates/Traditional_Chinese_Big5-ap_transaction.tex
/var/lib/sql-ledger/templates/Traditional_Chinese_Big5-ar_transaction.tex
/var/lib/sql-ledger/templates/Traditional_Chinese_Big5-bin_list.tex
/var/lib/sql-ledger/templates/Traditional_Chinese_Big5-check.tex
/var/lib/sql-ledger/templates/Traditional_Chinese_Big5-credit_invoice.tex
/var/lib/sql-ledger/templates/Traditional_Chinese_Big5-credit_note.tex
/var/lib/sql-ledger/templates/Traditional_Chinese_Big5-debit_invoice.tex
/var/lib/sql-ledger/templates/Traditional_Chinese_Big5-debit_note.tex
/var/lib/sql-ledger/templates/Traditional_Chinese_Big5-invoice.tex
/var/lib/sql-ledger/templates/Traditional_Chinese_Big5-letterhead.tex
/var/lib/sql-ledger/templates/Traditional_Chinese_Big5-packing_list.tex
/var/lib/sql-ledger/templates/Traditional_Chinese_Big5-pick_list.tex
/var/lib/sql-ledger/templates/Traditional_Chinese_Big5-purchase_order.tex
/var/lib/sql-ledger/templates/Traditional_Chinese_Big5-receipt.tex
/var/lib/sql-ledger/templates/Traditional_Chinese_Big5-remittance_voucher.tex
/var/lib/sql-ledger/templates/Traditional_Chinese_Big5-request_quotation.tex
/var/lib/sql-ledger/templates/Traditional_Chinese_Big5-sales_order.tex
/var/lib/sql-ledger/templates/Traditional_Chinese_Big5-sales_quotation.tex
/var/lib/sql-ledger/templates/Traditional_Chinese_Big5-statement.tex
/var/lib/sql-ledger/templates/Traditional_Chinese_Big5-timecard.tex
/var/lib/sql-ledger/templates/Traditional_Chinese_Big5-work_order.tex
/var/lib/sql-ledger/templates/Traditional_Chinese_UTF8-ap_transaction.tex
/var/lib/sql-ledger/templates/Traditional_Chinese_UTF8-ar_transaction.tex
/var/lib/sql-ledger/templates/Traditional_Chinese_UTF8-bin_list.tex
/var/lib/sql-ledger/templates/Traditional_Chinese_UTF8-check.tex
/var/lib/sql-ledger/templates/Traditional_Chinese_UTF8-credit_invoice.tex
/var/lib/sql-ledger/templates/Traditional_Chinese_UTF8-credit_note.tex
/var/lib/sql-ledger/templates/Traditional_Chinese_UTF8-debit_invoice.tex
/var/lib/sql-ledger/templates/Traditional_Chinese_UTF8-debit_note.tex
/var/lib/sql-ledger/templates/Traditional_Chinese_UTF8-invoice.tex
/var/lib/sql-ledger/templates/Traditional_Chinese_UTF8-letterhead.tex
/var/lib/sql-ledger/templates/Traditional_Chinese_UTF8-packing_list.tex
/var/lib/sql-ledger/templates/Traditional_Chinese_UTF8-pick_list.tex
/var/lib/sql-ledger/templates/Traditional_Chinese_UTF8-purchase_order.tex
/var/lib/sql-ledger/templates/Traditional_Chinese_UTF8-receipt.tex
/var/lib/sql-ledger/templates/Traditional_Chinese_UTF8-remittance_voucher.tex
/var/lib/sql-ledger/templates/Traditional_Chinese_UTF8-request_quotation.tex
/var/lib/sql-ledger/templates/Traditional_Chinese_UTF8-sales_order.tex
/var/lib/sql-ledger/templates/Traditional_Chinese_UTF8-sales_quotation.tex
/var/lib/sql-ledger/templates/Traditional_Chinese_UTF8-statement.tex
/var/lib/sql-ledger/templates/Traditional_Chinese_UTF8-timecard.tex
/var/lib/sql-ledger/templates/Traditional_Chinese_UTF8-work_order.tex
/var/lib/sql-ledger/templates/Brazilian_Portuguese-pos_invoice.txt
/var/lib/sql-ledger/templates/Danish-pos_invoice.txt
/var/lib/sql-ledger/templates/Default-pos_invoice.txt
/var/lib/sql-ledger/templates/Dutch-pos_invoice.txt
/var/lib/sql-ledger/templates/Estonian-pos_invoice.txt
/var/lib/sql-ledger/templates/Estonian_UTF8-pos_invoice.txt
/var/lib/sql-ledger/templates/French-pos_invoice.txt
/var/lib/sql-ledger/templates/German-pos_invoice.txt
/var/lib/sql-ledger/templates/Hungarian-pos_invoice.txt
/var/lib/sql-ledger/templates/Italian-pos_invoice.txt
/var/lib/sql-ledger/templates/Norwegian-pos_invoice.txt
/var/lib/sql-ledger/templates/Russian-pos_invoice.txt
/var/lib/sql-ledger/templates/Service-pos_invoice.txt
/var/lib/sql-ledger/templates/Slovak-pos_invoice.txt
/var/lib/sql-ledger/templates/Spanish_A4-pos_invoice.txt
/var/lib/sql-ledger/templates/Spanish_Letter-pos_invoice.txt
/var/lib/sql-ledger/templates/Swedish-pos_invoice.txt
/var/lib/sql-ledger/templates/Traditional_Chinese_Big5-pos_invoice.txt
/var/lib/sql-ledger/templates/Traditional_Chinese_UTF8-pos_invoice.txt
/var/lib/sql-ledger/templates/Brazilian_Portuguese-logo.eps
/var/lib/sql-ledger/templates/Danish-logo.eps
/var/lib/sql-ledger/templates/Default-logo.eps
/var/lib/sql-ledger/templates/Dutch-logo.eps
/var/lib/sql-ledger/templates/Estonian-logo.eps
/var/lib/sql-ledger/templates/Estonian_UTF8-logo.eps
/var/lib/sql-ledger/templates/French-logo.eps
/var/lib/sql-ledger/templates/German-logo.eps
/var/lib/sql-ledger/templates/Hungarian-logo.eps
/var/lib/sql-ledger/templates/Italian-logo.eps
/var/lib/sql-ledger/templates/Norwegian-logo.eps
/var/lib/sql-ledger/templates/Russian-logo.eps
/var/lib/sql-ledger/templates/Service-logo.eps
/var/lib/sql-ledger/templates/Slovak-logo.eps
/var/lib/sql-ledger/templates/Spanish_A4-logo.eps
/var/lib/sql-ledger/templates/Spanish_Letter-logo.eps
/var/lib/sql-ledger/templates/Swedish-logo.eps
/var/lib/sql-ledger/templates/Traditional_Chinese_Big5-logo.eps
/var/lib/sql-ledger/templates/Traditional_Chinese_UTF8-logo.eps
/var/lib/sql-ledger/templates/Brazilian_Portuguese-logo.png
/var/lib/sql-ledger/templates/Danish-logo.png
/var/lib/sql-ledger/templates/Default-logo.png
/var/lib/sql-ledger/templates/Dutch-logo.png
/var/lib/sql-ledger/templates/Estonian-logo.png
/var/lib/sql-ledger/templates/Estonian_UTF8-logo.png
/var/lib/sql-ledger/templates/French-logo.png
/var/lib/sql-ledger/templates/German-logo.png
/var/lib/sql-ledger/templates/Hungarian-logo.png
/var/lib/sql-ledger/templates/Italian-logo.png
/var/lib/sql-ledger/templates/Norwegian-logo.png
/var/lib/sql-ledger/templates/Russian-logo.png
/var/lib/sql-ledger/templates/Service-logo.png
/var/lib/sql-ledger/templates/Slovak-logo.png
/var/lib/sql-ledger/templates/Spanish_A4-logo.png
/var/lib/sql-ledger/templates/Spanish_Letter-logo.png
/var/lib/sql-ledger/templates/Swedish-logo.png
/var/lib/sql-ledger/templates/Traditional_Chinese_Big5-logo.png
/var/lib/sql-ledger/templates/Traditional_Chinese_UTF8-logo.png
/var/lib/sql-ledger/users
/var/lib/sql-ledger/users/sql-ledger.eps
/var/lib/sql-ledger/users/sql-ledger.png
/var/lib/sql-ledger/css
/var/lib/sql-ledger/css/sql-ledger-blue.css
/var/lib/sql-ledger/css/sql-ledger-brown.css
/var/lib/sql-ledger/css/sql-ledger-purple.css
/var/lib/sql-ledger/css/sql-ledger-red.css
/var/lib/sql-ledger/css/sql-ledger-yellow.css
/var/lib/sql-ledger/css/sql-ledger.css
/usr/share/sql-ledger/sql-ledger.conf
/usr/share/sql-ledger/templates
/usr/share/sql-ledger/users
/usr/share/sql-ledger/css
/usr/lib/sql-ledger
jacob@jacob-laptop:~$ 

```

I don't see a .bin file. Will this program install through "add/remove" or "package manager"?

---

### Post by i.r.id10t on 2009-08-27
Looks like it runs via a webserver... try opening a browser and going to [http://localhost](http://localhost)

---

### Post by oceanfirehawk on 2009-08-27
> **i.r.id10t said:**
> Looks like it runs via a webserver... try opening a browser and going to [http://localhost](http://localhost)

All the Firefox browser said when I entered [http://localhost](http://localhost) is

"It works!"

---

### Post by unutbu on 2009-08-27
I've downloaded sql-ledger and I think I managed to get it to work.
I don't know if this is how they intended you to get it to work, but
this is what I did:
```

sudo ln -s /etc/sql-ledger/sql-ledger-httpd.conf /etc/apache2/conf.d/sql-ledger-httpd.conf
```

This makes a symlink from /etc/apache2/conf.d/sql-ledger-httpd.conf to
/etc/sql-ledger/sql-ledger-httpd.conf.
```

sudo /etc/init.d/apache2 restart

```
Then point your browser at 

[http://localhost/sql-ledger/](http://localhost/sql-ledger/)

Since you do not have a user setup yet, 
click the Administration Login link at the bottom.
Use your normal user password to login. 

From there you should see the "SQL-Ledger Accounting Administration" page.

---

### Post by oceanfirehawk on 2009-08-27
> **unutbu said:**
> I've downloaded sql-ledger and I think I managed to get it to work.
I don't know if this is how they intended you to get it to work, but
this is what I did:
```

sudo ln -s /etc/sql-ledger/sql-ledger-httpd.conf /etc/apache2/conf.d/sql-ledger-httpd.conf
```

This makes a symlink from /etc/apache2/conf.d/sql-ledger-httpd.conf to
/etc/sql-ledger/sql-ledger-httpd.conf.
```

sudo /etc/init.d/apache2 restart

```
Then point your browser at 

[http://localhost/sql-ledger/](http://localhost/sql-ledger/)

Since you do not have a user setup yet, 
click the Administration Login link at the bottom.
Use your normal user password to login. 

From there you should see the "SQL-Ledger Accounting Administration" page.

Worked like a charm: The only other question is what values I put in the following areas under add user-database

see pic   ----if i dont put anything for dataset it gives me an error message.

---

### Post by unutbu on 2009-08-27
Well, I've never used sql-ledger, so what I'm suggesting comes mainly from 
/usr/share/doc/sql-ledger/README.gz, and from fooling around:
```

sudo apt-get install postgresql
```
```

postgres@farmer:/home/unutbu$ createuser -d -P sql-ledger
Enter password for new role: 
Enter it again: PASSWORD

Shall the new role be a superuser? (y/n) n
Shall the new role be allowed to create more new roles? (y/n) n

```
Point browser at 
[http://localhost/sql-ledger/](http://localhost/sql-ledger/)

Click "Administration Login"
Click "Login" (no password necessary)
Click "Pg Database Administration"

Enter```

Host: localhost
User: sql-ledger
Connect to: template1
Password: PASSWORD
```
 
Click "Create Dataset"

Create Dataset: test
Click "Continue"

At the main menu,
Click "Add User"
```

Login: testuser
Password: testuser
Driver: PG
Dataset: test
User: sql-ledger
Host: localhost
Password: PASSWORD

```

---

### Post by oceanfirehawk on 2009-10-27
> **unutbu said:**
> Well, I've never used sql-ledger, so what I'm suggesting comes mainly from 
/usr/share/doc/sql-ledger/README.gz, and from fooling around:
```

sudo apt-get install postgresql
```
```

postgres@farmer:/home/unutbu$ createuser -d -P sql-ledger
Enter password for new role: 
Enter it again: PASSWORD

Shall the new role be a superuser? (y/n) n
Shall the new role be allowed to create more new roles? (y/n) n

```
Point browser at 
[http://localhost/sql-ledger/](http://localhost/sql-ledger/)

Click "Administration Login"
Click "Login" (no password necessary)
Click "Pg Database Administration"

Enter```

Host: localhost
User: sql-ledger
Connect to: template1
Password: PASSWORD
```
 
Click "Create Dataset"

Create Dataset: test
Click "Continue"

At the main menu,
Click "Add User"
```

Login: testuser
Password: testuser
Driver: PG
Dataset: test
User: sql-ledger
Host: localhost
Password: PASSWORD

```

Thanks for all the help. This program seems kinda to much for my needs. But you helped me to get it working!

---

### Post by phillw on 2009-10-27
From Synaptics, the following are decent GUI apps to have a play with MySQL with ....

MySQL Administrator 
MySQL Browser

Once you have MySQL installed, you can issue commands from a terminal

[http://www.brainbell.com/tutorials/MySQL/MySQL_Tools.htm](http://www.brainbell.com/tutorials/MySQL/MySQL_Tools.htm)

Has a brief introduction to the above.

Regards,

Phill.

---

