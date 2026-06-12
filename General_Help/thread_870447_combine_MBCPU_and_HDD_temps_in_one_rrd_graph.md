---
title: "combine MB/CPU and HDD temps in one rrd graph"
date: 2008-07-25
forum: General Help
---

### Post by graysky on 2008-07-25
Can someone with RRD experience help me combine my MB, CPU and HDD temp into one graph?  I'm just not well versed in these rrd files to save my life.  I'm thinking that some how, they need to combined into a single rrd_combined.pl and have the graph output show all 3 on the same axis.

**rrd_MBtemp.pl**
```
#!/usr/bin/perl
#
#  rrd_MBtemp.pl
#	Motherboard Temperature data collection routine for KnoppMyth
#
########################################################################
# Configuration:
my $dbf = 'MBtemp';
my $configfile = '/etc/rrd.config';
########################################################################
use RRDs;

if (! -d "/myth") { $configfile = "./D_rrd.config"; }	# DEBUG
do $configfile;

sub create {
    #	$_[0] = filename
    if (! -e "$log/$_[0].rrd") {
	print "Create db for $_[0] => $log/$_[0].rrd\n";
	RRDs::create( "$log/$_[0].rrd", "-s 300",
	    "DS:mbt1:GAUGE:600:0:U",
	    "DS:mbt2:GAUGE:600:0:U",
	    "DS:mbt3:GAUGE:600:0:U",
	    "RRA:AVERAGE:0.5:1:576",
	    "RRA:AVERAGE:0.5:6:672",
	    "RRA:AVERAGE:0.5:24:732",
	    "RRA:AVERAGE:0.5:144:1460");
	$ERROR = RRDs::error;
	print "Error: RRDs::create failed for '$_[0]' : $ERROR\n" if $ERROR;
    }
}

my ($mbt1, $mbt2);

sub gather {
    $mbt1 = `$MBT_prog | grep "M/B Temp" | cut -c 15-17`; 
    $mbt2 = `$MBT_prog | grep "CPU Temp" | cut -c 15-17`;
    $mbt3 = `$MBT_prog|grep -i "aux temp" |cut -c 13-17`; 
    $mbt1 =~ s/[\n ]//g;
    $mbt2 =~ s/[\n ]//g;
    $mbt3 =~ s/[\n ]//g;
    print "$dbf: motherboard $mbt1, CPU $mbt2, case $mbt3, °C\n";
    # The motherboard sensor occasionally returns nonsense values.
    # This should keep the spurious peaks from roaching the graph...
    if ($mbt1 > 100.0) { $mbt1 = $mbt2 }
    print "$dbf: motherboard $mbt1, CPU $mbt2, case $mbt3, °C\n";
}

sub update {
    #	$_[0] = filename
    RRDs::update( "$log/$_[0].rrd", "-t",
	"mbt1:mbt2:mbt3",
	"N:$mbt1:$mbt2:$mbt3");
    $ERROR = RRDs::error;
    print "Error: RRDs::update for '$_[0]' : $ERROR\n" if $ERROR;
}

#°
sub graph {
    #	$_[0] = time interval (ie: day...)
    #	$_[1] = filename suffix.
    RRDs::graph( "$png/$dbf-$_[1].png", "-s -1$_[0]", "-aPNG",
	"-w $Gwd", "-h $Ght", "-E", "-l 20", "-M",
	"--color", "SHADEA$color",
	"--color", "SHADEB$color",
	"--color", "BACK$color",
	"-t Motherboard & CPU temperature degrees C :: $_[0]",
	"DEF:mbt1=$log/$dbf.rrd:mbt1:AVERAGE",
	"DEF:mbt2=$log/$dbf.rrd:mbt2:AVERAGE",
	"LINE1:mbt1$color_mbt1: MB temp\\:",
	"GPRINT:mbt1:MIN:Minimum\\: % 5.1lf",
	"GPRINT:mbt1:MAX:Maximum\\: % 5.1lf",
	"GPRINT:mbt1:AVERAGE:Average\\: % 5.1lf",
	"GPRINT:mbt1:LAST:Current\\: % 5.1lf °C\\j",
	"LINE1:mbt2$color_mbt2:CPU temp\\:",
	"GPRINT:mbt2:MIN:Minimum\\: % 5.1lf",
	"GPRINT:mbt2:MAX:Maximum\\: % 5.1lf",
	"GPRINT:mbt2:AVERAGE:Average\\: % 5.1lf",
	"GPRINT:mbt2:LAST:Current\\: % 5.1lf °C\\j");
    $ERROR = RRDs::error;
    print "Error: RRDs::graph failed for '$_[0]' : $ERROR\n" if $ERROR;
}
########################################################################
create "$dbf";
gather;
update "$dbf";
graph 'day',   'Daily';
graph 'week',  'Weekly';
graph 'month', 'Monthly';
graph 'year',  'Yearly';
graph '2hour', '12hourly';
########################################################################
# vim: sw=4 ts=8
# End
```

**rrd_HDtemp.pl**
```
#!/usr/bin/perl
#
#  rrd_HDtemp.pl
#       Disk temperature data collection routine for KnoppMyth
#
########################################################################
# Configuration:
my $dbf = "HDtemp";
my $configfile = '/etc/rrd.config';
my @temps;
########################################################################
use RRDs;

if (! -d "/myth") { $configfile = "./D_rrd.config"; }   # DEBUG
do $configfile;

sub create {
    #   $_[0] = filename
    if (! -e "$log/$_[0].rrd") {
        print "Create db for $_[0] => $log/$_[0].rrd\n";
        push @args, "$log/$_[0].rrd";
        push @args, "-s 300";
        @devs = split /\s+/, $HDT_dev;
        for($i = 0; $i < scalar(@devs); $i++) {
          push @args, "DS:hdt" . ($i + 1) . ":GAUGE:600:0:U";
        }
        push @args, "RRA:AVERAGE:0.5:1:576";
        push @args, "RRA:AVERAGE:0.5:6:672";
        push @args, "RRA:AVERAGE:0.5:24:732";
        push @args, "RRA:AVERAGE:0.5:144:1460";
        RRDs::create(@args);
        $ERROR = RRDs::error;
        print "Error: RRDs::create failed for '$_[0]' : $ERROR\n" if $ERROR;
    }
}


sub gather {
    my ($dev, $hdt1, $hdtT, $hdtD, $res);
    # device names in $_[0]
    $res = "$dbf:";
    undef @temps;
    @devs = split /\s+/, $_[0];
    foreach $_ (@devs) {
        $dev = "/dev/$_";
        my $line = `/usr/sbin/hddtemp -q $dev`;
        chomp( $line );
        my ( $devN, $devD, $devT ) = split( /\:\s+/, $line );
        #print "HDtemp $_[0]: '$devN' '$devD' '$devT'\n";
        my ( $dev1, $dev2 ) = split( /\s+or\s+/, $devT );
        #print "HDtemp $_[0]: '$dev1' '$dev2'\n";
        ( $hdt1, $hdtT ) = split( /\s+/, $dev1 );
        #print "HDtemp $_[0]: '$hdt1' '$hdtT'\n";
        if ($devN ne $dev) {
            $hdt1 = 0; $hdtT = '?'; $hdtD = '';
        } else {
            $hdtD = $devD;
        }
        if ("$hdtT" eq "") {$hdt1 = "C"; }
        $out .= "$_: $hdt1, ";
        push @temps, $hdt1;
    }
    chop $out; # remove extra space
    chop $out; # remove extra comma
    print "$out\n";
}

sub update {
    #   $_[0] = filename
    my($str1, $str2);
    $str1 = '';
    $str2 = 'N:';
    for($i = 0; $i < scalar(@temps); $i++) {
      $str1 .= ("hdt" . ($i + 1) . ":");
      $str2 .= ($temps[$i] . ":");
    }
    chop $str1; # Get rid of last colon
    chop $str2; # Get rid of last colon
    RRDs::update("$log/$_[0].rrd", "-t", $str1, $str2);
    print "$str1\n$str2\n";
    $ERROR = RRDs::error;
    print "Error: RRDs::update for '$_[0]' : $ERROR\n" if $ERROR;
}

sub graph {
    #   $_[0] = time interval (ie: day...)
    #   $_[1] = filename suffix.
    undef @args;
    @devs = split /\s+/, $HDT_dev;
    @args = ( "$png/$dbf-$_[1].png", "-s -1$_[0]", "-aPNG",
        "-w $Gwd", "-h $Ght", "-E", "-l 20", "-M",
        "--color", "SHADEA$color",
        "--color", "SHADEB$color",
        "--color", "BACK$color",
        "-t Disk temperature :: $_[0]");
    for($i = 0; $i < scalar(@temps); $i++) {
        push @args, "DEF:hdt" . ($i + 1) . "=$log/$dbf.rrd:hdt" . ($i + 1) . ":AVERAGE";
        push @args, "LINE1:hdt" . ($i+1) . "$HDT_colors[$i]: $devs[$i] degrees C\\:",
        "GPRINT:hdt" . ($i + 1) . ":MIN:Minimum\\: %.0lf",
        "GPRINT:hdt" . ($i + 1) . ":MAX:Maximum\\: %.0lf",
        "GPRINT:hdt" . ($i + 1) . ":AVERAGE:Average\\: %.2lf",
        "GPRINT:hdt" . ($i + 1) . ":LAST:Current\\: %.1lf\\j";
    }
    RRDs::graph(@args);
    $ERROR = RRDs::error;
    print "Error: RRDs::graph failed for '$_[0]' : $ERROR\n" if $ERROR;
}
########################################################################
create "$dbf";
gather "$HDT_dev";
update "$dbf";
graph 'day',   'Daily';
graph 'week',  'Weekly';
graph 'month', 'Monthly';
graph 'year',  'Yearly';
graph '2hour', '12hourly';
########################################################################
# vim: sw=4 ts=8
# End
```

---

