---
title: "errors with &gt; apt-get update --fix-missing"
date: 2009-02-24
forum: Installation &amp; Upgrades
---

### Post by serros88 on 2009-02-24
root@inspiron6400:/home/serros# apt-get update --fix-missing
Hit [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) intrepid Release.gpg
Hit [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) intrepid-updates Release.gpg                  
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid Release.gpg                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg                   
Hit [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) intrepid Release                    
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release.gpg [307B]                     
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid Release                              
Hit [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) intrepid-updates Release                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release                       
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release [27.6kB]            
Hit [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) intrepid/main Packages             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release                         
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Packages            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Packages       
Hit [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) intrepid/restricted Packages        
Hit [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) intrepid/main Sources                         
Hit [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) intrepid/restricted Sources                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                            
Hit [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) intrepid/universe Packages                    
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Sources                      
Hit [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) intrepid/universe Sources                     
Hit [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) intrepid/multiverse Packages        
Hit [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) intrepid/multiverse Sources         
Hit [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) intrepid-updates/main Packages      
Hit [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) intrepid-updates/restricted Packages
Hit [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) intrepid-updates/main Sources       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Packages 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Sources        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Sources  
Hit [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) intrepid-updates/restricted Sources 
Hit [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) intrepid-updates/universe Packages  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                  
Hit [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) intrepid-updates/universe Sources   
Hit [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) intrepid-updates/multiverse Packages
Hit [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) intrepid-updates/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Sources
Fetched 308B in 0s (798B/s)

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 60D11217247D1CFF
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

Thanks for help.
serros

---

### Post by binbash on 2009-02-24
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

make it executable (chmod +x filename.pl) then run it via : 

perl change.pl

---

### Post by serros88 on 2009-02-25
Where the file "change.pl" should be located? 
Cheers. 
Serge

---

### Post by forger on 2009-02-27
Use these instructions for the updated script:
[http://ubuntuforums.org/showthread.php?t=1056099](http://ubuntuforums.org/showthread.php?t=1056099)

---

