---
title: "Software sources problems!"
date: 2009-02-20
forum: Installation &amp; Upgrades
---

### Post by Ratscallion on 2009-02-20
Hi all. I am trying to update my Software Sources in the built in Software Sources GUI. I have the sources for the most commonly used programs, I can list them if you need me to. My problem is the following, when I reload the Software Sources when I close it, it gives me an error message. It is the following: 
> W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 60D11217247D1CFF
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 665F9AEFE1098513
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6AF0E1940624A220
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 632D16BB0C713DA6
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7889D725DA6DEEAAI have no idea what this is supposed to mean, or how I can prevent it from happening. If anyone could point me in the right direction, I would be very gratfull. Thanks.

By the way, I am using Ubuntu 8.10 Intrepid on Wubi.

---

### Post by howefield on 2009-02-20
Try the answer in this thread..

[http://ubuntuforums.org/showthread.php?t=1046158](http://ubuntuforums.org/showthread.php?t=1046158)

---

### Post by binbash on 2009-02-20
save this as change.pl : 

```

#!/usr/bin/env perl
# Perl script to fix Launchpad PPA links and import required keys.
# VERSION: 1.2
#
# Requires: HTML::Parser IO::Socket::SSL
# sudo apt-get install libhtml-parser-perl libio-socket-ssl-perl
#
# Copyright (c) 2009 Savvas Radevic <vicedar@gmail.com>
#
# This program is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with this program.  If not, see <http://www.gnu.org/licenses/>.
#
# UPDATES:
# 1.2:
#    * Added md5sum check for sources.list
#    * Added support for /etc/apt/sources.list.d/*.list
# 1.1:
#    * Added support for key format in edge.launchpad.net server.
#    * Needs IO::Socket::SSL
#
# Do NOT edit unless you know what you're doing!

use strict;
use LWP::Simple qw(get);
use Digest::file qw(digest_file_hex);

my $aptdir = '/etc/apt';
my $sourcelist = $aptdir.'/sources.list';
my $sourceparts = $aptdir.'/sources.list.d';
my $backupext = '.backup';
my $tmpfilename = '/tmp/lp_change.list';
my @lplink = ('http://launchpad.net/~','/+archive/ppa');
my (@allsources, @lpusers);

# Return .list files
@allsources = grep{ -f $_ and /\.list$/ } glob("$sourceparts/*");
# Add main source
if (-f $sourcelist) { push(@allsources, $sourcelist); }
print("Found apt source list files:\n  ".join("\n  ",@allsources)."\n");

foreach my $filename (@allsources) {
    my @new = ();
    print("\nChecking file $filename\n");
    open(S, $filename) or die $!;
    foreach my $l (<S>) {
        if ($l =~ m!^deb(?:-src)?\s+http://ppa.launchpad.net/(\S+)/ubuntu!i) {
            my $r = $1;
            if ($r !~ m!/ppa$!i) {
                $r =~ s!$!/ppa!i;
                $l =~ s!^(deb(?:-src)?\s+http://ppa.launchpad.net/)\S+(/ubuntu)!${1}${r}${2}!i;
                print("Detected/Fixed: $l");
            }
            else {
                print("Detected/Correct: $l");
            }
            $r =~ s!/ppa$!!i;
            # Look if user $r is already on @lpusers - if not, add
            my %lookup = map { $_ => undef } @lpusers;
            if (not exists $lookup{$r}) { push(@lpusers, $r); }
        }
        push(@new, $l);
    }

    close(S);
    open(W, ">$tmpfilename") or die $!;
    print W @new;
    close(W);
    if (digest_file_hex($tmpfilename, "MD5") != digest_file_hex($filename, "MD5")) {
        print("Detected differences between $tmpfilename and $filename\n");
        print("Moving temporary file as $filename\n");
        print("INFO: Enter your administrator password if asked\n\n");
        my @s = ('sudo', 'cp', '-f', $filename, $filename.$backupext);
        system(@s) == 0 or die("system @s failed: $?\n");
        my @s = ('sudo', 'mv', $tmpfilename, $filename);
        system(@s) == 0 or die("system @s failed: $?\n");
    }
    else {
        print("No change for $filename\n");
    }
}

if (defined(@lpusers)) {
    print("Will retrieve keys for: @lpusers\n");
}
else {
    print("\nNo Launchpad PPA links/users detected, exiting.\n");
}

my $getkey = GetKey->new;
foreach my $u (@lpusers) {
    my $url = $lplink[0].$u.$lplink[1];
    print("Attempting to get Launchpad key for $u: $url\n");
    my $html = get($url);
    $getkey->parse($html);
}


package GetKey;
use base qw(HTML::Parser);
use IO::Socket::SSL;
my ($div_tag, $code_tag);
sub start {
    my ($self, $tag, $attr, $attrlist, $origtext) = @_;
    # If HTML tag is "a" (or "A")
    if ($tag =~ /^div$/i and $attr->{id} and $attr->{id} eq 'signing-key') {
        $div_tag = 1;
    }
    elsif ($tag =~ /^code$/i and $div_tag) {
        $code_tag = 1;
    }
}
sub text {
    my ($self, $plaintext) = @_;
    # If we're in the anchor tag, and text is "http" or "ftp"
    if ($div_tag and $code_tag) {
        #New LP uses 1024R/247D1CFF instead of D2BB86E0EBD0F0A43D4DB3A760D11217247D1CFF format
        if ($plaintext =~ m!/([\w\d]+)!i) { $plaintext = $1; }
        print("Found key: $plaintext\n");
        &importkey($plaintext);
    }
}
sub end {
    my ($self, $tag, $origtext) = @_;
    if ($tag =~ /^div$/i) { $div_tag = 0; }
    elsif ($tag =~ /^code$/i) { $code_tag = 0; }
}
sub importkey {
    my ($key) = @_;
    print("Adding $key to your username's gpg\n");
    my @a = ('gpg', '--keyserver', 'keyserver.ubuntu.com', '--recv-keys', $key);
    system(@a) == 0 or print("system @a failed: $?\n");
    
    print("Adding key to apt\n");
    my $b = "gpg --export --armor $key | sudo apt-key add -";
    print("INFO: Enter your administrator password if asked\n\n");
    my $command = `$b`;
    print("$command\n");
}

```

then :

chmod +x change.pl
then run it via : 

perl change.pl

---

### Post by forger on 2009-02-20
> **binbash said:**
> save this as change.pl : 
[...]
then :

chmod +x change.pl
then run it via : 

perl change.pl

Or get it from here: [http://ubuntuforums.org/showthread.php?t=1056099](http://ubuntuforums.org/showthread.php?t=1056099)
:)

---

### Post by Ratscallion on 2009-02-21
Thanks for all of your help people. My sources are working as usual now! Thanks a lot.:D:D:D

---

### Post by jherskow on 2009-07-20
im pretty new to all this.
ive been adding different sources lately to get some drivers that i need, and i recently added ubuntu tweak to help update my sources to get stuff like skype.

however, the sources seem to have trouble updating, and the error message is as follows:
[I][SIZE=1]
[/SIZE][/I][INDENT]*[SIZE=1]W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures were invalid: BADSIG EF4186FE247510BE Launchpad PPA for Ubuntu Mozilla Daily Build Team[/SIZE]*

*[SIZE=1]W: GPG error: [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) jaunty Release: The following signatures were invalid: NODATA 1 NODATA 2[/SIZE]*
*[SIZE=1]W: Failed to fetch [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu/dists/jaunty/Release](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu/dists/jaunty/Release)  [/SIZE]*

*[SIZE=1]W: Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/jaunty/free/binary-i386/Packages.bz2](http://medibuntu.sos-sts.com/repo/dists/jaunty/free/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)[/SIZE]*

*[SIZE=1]W: Some index files failed to download, they have been ignored, or old ones used instead.[/SIZE]*

[/INDENT]pleaseanybodyhelp- (total newbie)

thanks!

---

### Post by Ratscallion on 2009-07-20
Ubuntu Tweak tends to mess up your sources, as I found out the hard way. To get some of the apps that Ubuntu Tweak offes, I recommend going to the official site and either grabbing the source/.deb file or adding the official repository. You can then also delete/disable the Ubuntu Tweak sources in software sources. Once it's all done, just run a sudo apt-get update && sudo apt-get upgrade

---

