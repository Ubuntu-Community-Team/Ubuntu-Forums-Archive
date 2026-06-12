---
title: "Perl error when talking to GPSD"
date: 2011-02-01
forum: Hardware
---

### Post by Joe Sun on 2011-02-01
[SIZE=4]I want to use usb-gps to get my current location. I installed GPSD and it seems working well.(When I use xgps, I can get my coordinate).

But I execute the following code :

[SIZE=2]#!/usr/bin/perl -w
use IO::Socket;
use Socket;

my $sock = new IO::Socket::INET (
        PeerAddr => 'localhost',
        PeerPort => '2947',
        Proto => 'tcp');

die "Could not create socket: $!\n" unless $sock;

print $sock "p\n";

$line = <$sock>;

chomp $line;
$coords1 = (split (',', $line))[1];
$coords = (split ('=', $coords1))[1];
($lat, $long) = split(" ", $coords);
print "$lat, $long\n";
close ($sock);


[/SIZE]The terminal says:

 [SIZE=2]joe@ubuntu:~/Desktop$ ./gps.pl
Use of uninitialized value $coords in split at ./gps.pl line 19, <GEN0> line 1.
Use of uninitialized value $lat in concatenation (.) or string at ./gps.pl line 20, <GEN0> line 1.
Use of uninitialized value $long in concatenation (.) or string at ./gps.pl line 20, <GEN0> line 1.
, 


[SIZE=4]The gps seems no problem, can you help me how to fix the code?
Thanks a million~
[/SIZE][/SIZE][/SIZE]

---

