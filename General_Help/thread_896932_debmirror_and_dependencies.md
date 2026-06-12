---
title: "debmirror and dependencies"
date: 2008-08-21
forum: General Help
---

### Post by SteelWo1f on 2008-08-21
Hi

I want to be able to build a local repository of a select few packages. The problem is how do I use debmirror to get a package and all its dependencies? If there is an easy way to get a list of dependencies, then I can just get them one at a time in a script. Is there something other then debmirror that I should use?

Any thoughts?

Thanks

Jonathan Steel

---

### Post by tytiiiore on 2008-09-06
bump up lurkWho's 50 Cents&#12288;&#12288;Jacky: I found 50 cents on the sidewalk in front of school.&#12288;&#12288;Tommy: I think it's mine. I dropped 50 cents there today and couldn't find it.&#12288;&#12288;Jacky: But what I found was two quarters.&#12288;&#12288;Tommy: Then I'm sure it's mine. It probably broke when it hit the sidewalk.Welcome to our website for you World of Warcraft Gold,Wow Gold,Cheap World of Warcraft Gold,buy cheap wow Power Leveling,real wow gold,sell wow gold, ... *Supply Cheap [WoW Gold](http://www.wowgoldlive.com) to our loyal customers. Buy [WoW Gold](http://www.gamelee.de),cheap [aoc gold](http://www.aocgoldweb.com), now, we have available stock of [aoc power leveling](http://www.aocpowerleveling-gold.com),on most of the servers. We can provide really cheap [World of warcraft Power Leveling](http://www.wow-powerleveling.org/wow+power+leveling.html). Enjoy a new life, We are a world class wow Power Leveling store online !*

---

### Post by glinsvad on 2008-11-27
Presumably the dependencies have to be resolved using apt-get somehow. I suggest you try using the --download-only option and check out /var/cache/apt/archives.

---

### Post by SteelWo1f on 2008-11-27
Hmmm. Thats a good idea. Thanks. I think with a little scripting, that way could work.

As it is, I've concocted a bunch of scripts that use dpkg in combination with apt-get in order to recursively figure out the dependencies and download everything that is needed. Those are then moved into a repository and I build up the repo. If anyone is interested, here was the script I used. You will need to build a mirrorbuild.sh script, the instructions for which I found on another site.
> 
#!/usr/bin/perl

use warnings;
use strict;

sub getDeps($) {
    my $pkg = shift @_;
    my @ret;
    #return `apt-cache depends $pkg | grep Depends | awk '{ print \$2 }'`;
    my @deps = `apt-cache depends $pkg`;

    foreach my $dep ( @deps ) {
        if ( $dep =~ m/^.*Depends: ([^<>]*)$/ ) {
            my $newDep = $1;
            chomp $newDep;
            push @ret, $newDep;
        }
    }
    return @ret;
}

my $pkg = $ARGV[0];
my %depends;
my @getDepends;

print STDERR "Getting package: $pkg\n";

print STDERR "Calculating dependencies\n";

my @newDepends = ($pkg);
foreach my $curPkg ( @newDepends ) {
    print "Depends: $curPkg\n";
    push @getDepends, $curPkg;
    my @curDepends = getDeps($curPkg);
    foreach my $dep ( @curDepends ) {
        if ( !defined($depends{$dep}) ) {
            $depends{$dep} = 1;
            push @newDepends, $dep;
        }
    }
}

print STDERR "Getting packages\n";

my $include = "";
foreach my $pkg ( @getDepends ) {
    $include .= " --include=$pkg.*";
}

print STDERR "Include to mirrorbuild.sh: $include";
$include =~ s/\+/\\\+/;
if ( $ARGV[1] ne "t" ) {
    system("mirrorbuild.sh \"$include\"");
}


---

### Post by love007575 on 2009-01-05
[[color=black]ThinkGeek[/color]](http://www.geekideathing.com/)

---

### Post by tm002dy on 2009-01-08
&#19981;&#33021;&#31616;&#21333;&#30340;&#20174;&#23383;&#27597;&#21644;&#25968;&#23383;&#30340;&#25645;&#37197;&#21028;&#39321;&#28207;&#20845;&#21512;&#24425;&#20154;&#27665;&#24065;&#30340;&#30495;&#20551;&#12290;&#29616;&#24050;&#21457;&#34892;&#30340;&#20154;&#27665;&#24065;&#20896;&#23383;&#21495;&#20063;&#26377;HD90&#24320;&#22836;&#30340;&#65292;&#22240;&#27492;&#19981;&#33021;&#35828;&#20896;&#23383;&#21495;&#20197;HD90&#24320;&#22836;&#30340;&#37117;&#26159;&#20551;&#24065;&#12290; [&#39321;&#28207;&#20845;&#21512;&#24425;](http://www.tm262.org.cn)[&#39321;&#28207;&#20845;&#21512;&#24425;](http://www.tm262.ac.cn)[&#39321;&#28207;&#20845;&#21512;&#24425;](http://www.tm262.bj.cn)[&#39321;&#28207;&#20845;&#21512;&#24425;](http://www.tm262.sh.cn)[&#39321;&#28207;&#20845;&#21512;&#24425;&#32593;&#31449;](http://www.tm262.tj.cn)

---

