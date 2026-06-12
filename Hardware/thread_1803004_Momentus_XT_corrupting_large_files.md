---
title: "Momentus XT corrupting large files"
date: 2011-07-12
forum: Hardware
---

### Post by ironclaw on 2011-07-12
Update July 16, 2011: The instructions in this post are obsolete, and should not be used. If you want to reproduce the problem, please use the instructions that I have given in the [eighth post]("http://forums.seagate.com/t5/Momentus-XT-Momentus-Momentus/Momentus-XT-corrupting-large-files-Linux/m-p/109860#M3343") in the [Seagate Forums thread]("http://forums.seagate.com/t5/Momentus-XT-Momentus-Momentus/Momentus-XT-corrupting-large-files-Linux/td-p/109008").

I am crossposting [this post]("http://forums.seagate.com/t5/Momentus-XT-Momentus-Momentus/Momentus-XT-corrupting-large-files-Linux/td-p/109008") from the Seagate Community Forums because I found a [thread here]("http://ubuntuforums.org/showthread.php?t=1512288#15") with what might be a duplicate of my current problem. The original post:

I have had a major problem on three Momentus XT drives - large files (>2 GB) are often corrupted when written to the drive. More specifically, it seems that the drive occasionally 'forgets' to write chunks of data when multiple large files are written consecutively to the drive. For instance, writing multiple 4 GB files to a zero-filled Momentus XT drive often resulted in files that contained chunks of zero-filled data instead of the correct data.&#65279;
 
I'd like to know if any Linux user can reproduce this problem with the following steps:&#65279;
 
First we will select two directories for our test. (I recommend creating new directories to keep things clean.)&#65279; These directories should be mounted on devices with high bandwidth connections, such as SATA or eSATA.
```

export IN_DIR=<Directory not on Momentus XT>
export OUT_DIR=<Directory on Momentus XT>

```

Then we will create a 4 GB file of random data (using zeroes instead of random data may lead to an inconclusive test because some sectors of your drive may still be zero-filled from the factory). This will take some time (~10 minutes for me). Run "sudo killall -s USR1 dd" on another terminal to check the status.

```

sudo nice -n 19 dd if=/dev/urandom of=$IN_DIR/random_4g bs=1M count=4096

```

Now compute the SHA-1 checksum for this file, and save this to the selected $OUT_DIR directory.&#65279;
```

nice -n 19 sh -c "cd $IN_DIR && sha1sum ./random_4g" > $OUT_DIR/sha1sum_file

```

Now we will begin testing by executing the following loop:&#65279;
[LIST=1]
[*]Copy the 4 GB file to the selected $OUT_DIR directory on the Momentus XT.&#65279;
[*]Calculate the SHA-1 checksum and compare with what we found before.&#65279;
[*]Write result to both the terminal and a file.&#65279;
[/LIST]
```

nice -n 19 sh -c "cd $OUT_DIR; while true; do cp --backup=numbered $IN_DIR/random_4g ./ && sha1sum -c ./sha1sum_file | tee -a ./sha1sum_check; done"
(Note: code above should be on a single line; the forum might break it into two. Also, Ctrl+C to exit loop.)

```

Successive files are kept in the directory (via "--backup=numbered") instead of being overwritten to prevent in-place overwriting; in-place overwriting will lead to false-negatives. Make sure you don't run out of space - if you do, simply run
```

rm $OUT_DIR/random_4g*

```
to remove all the 4 GB files.&#65279; You can immediately continue testing afterwards.

The expected output from the loop is this:&#65279;
```

$ nice -n 19 sh -c "cd $OUT_DIR; while true; do cp --backup=numbered $IN_DIR/random_4g ./ && sha1sum -c ./sha1sum_file | tee -a ./sha1sum_check; done"
./random_4g: OK
./random_4g: OK
./random_4g: OK
./random_4g: OK
(etc.)

```

The (bad) output that I get is this:&#65279;
```

$ nice -n 19 sh -c "cd $OUT_DIR; while true; do cp --backup=numbered $IN_DIR/random_4g ./ && sha1sum -c ./sha1sum_file | tee -a ./sha1sum_check; done"
./random_4g: OK
./random_4g: FAILED
sha1sum: WARNING: 1 of 1 computed checksum did NOT match
./random_4g: FAILED
sha1sum: WARNING: 1 of 1 computed checksum did NOT match
./random_4g: FAILED
sha1sum: WARNING: 1 of 1 computed checksum did NOT match
(etc.)

```

It may take some time for the checksums to start failing - on one of my Momentus XT drives I had to loop through the test about 15 times before the checksum failed.&#65279;
 
My laptop should be stable - it has passed through 24 hours each of Memtest86+, Memtest86, and MPrime. I think that my SATA interface and controllers are also working correctly - I have done the same test on an Intel 320 series SSD and a Momentus 7200.4, and they both pass.&#65279;
 
Edited to add: The Momentus XT passes both the extended SMART test and "badblocks -w". (I haven't completed a SeaTools test because the bootable SeaTools crashes, and I don't have a Windows license.) Also, I have one Momentus XT drive right now - I have had three in total because I RMA'd twice.

---

