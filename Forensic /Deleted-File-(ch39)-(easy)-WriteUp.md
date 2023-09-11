# Deleted File WriteUp
1. Decompress the file as it was initialy compressed as tar & gzip.
```
x47@LAPTOP-J6FFFBS9:~$ gunzip ch39.gz
x47@LAPTOP-J6FFFBS9:~$ tar -xvf ch39
usb.image
```

2. Check the file type.
```
x47@LAPTOP-J6FFFBS9:~$ file usb.image
usb.image: DOS/MBR boot sector, code offset 0x3c+2, OEM-ID "mkfs.fat", sectors/cluster 4, reserved sectors 4, root entries 512, sectors 63488 (volumes <=32 MB), Media descriptor 0xf8, sectors/FAT 64, sectors/track 62, heads 124, hidden sectors 2048, reserved 0x1, serial number 0xc7ecde5b, label: "USB        ", FAT (16 bit)
```

3. List the files. Deleted files are marked with a `*`.
```
x47@LAPTOP-J6FFFBS9:~$ fls -r usb.image
r/r 3:  USB         (Volume Label Entry)
r/r * 5:        anonyme.png
v/v 1013699:    $MBR
v/v 1013700:    $FAT1
v/v 1013701:    $FAT2
V/V 1013702:    $OrphanFiles
```

4. List deleted files only.
```
x47@LAPTOP-J6FFFBS9:~$ fls -d -p usb.image
r/r * 5:        anonyme.png
```

5. Retrieve the deleted file anonyme.png with icat
```
x47@LAPTOP-J6FFFBS9:~$ icat usb.image 5 > ch39-anonyme.png
```

6. Use exiftool to see the meta data of the file to see if it contains the Creators full name.
```
x47@LAPTOP-J6FFFBS9:~$ exiftool ch39-anonyme.png
ExifTool Version Number         : 12.40
File Name                       : ch39-anonyme.png
Directory                       : .
File Size                       : 240 KiB
File Modification Date/Time     : 2023:09:11 11:56:28+02:00
File Access Date/Time           : 2023:09:11 11:56:28+02:00
File Inode Change Date/Time     : 2023:09:11 11:56:28+02:00
File Permissions                : -rw-r--r--
File Type                       : PNG
File Type Extension             : png
MIME Type                       : image/png
Image Width                     : 400
Image Height                    : 300
Bit Depth                       : 8
Color Type                      : RGB
Compression                     : Deflate/Inflate
Filter                          : Adaptive
Interlace                       : Noninterlaced
Gamma                           : 2.2
White Point X                   : 0.3127
White Point Y                   : 0.329
Red X                           : 0.64
Red Y                           : 0.33
Green X                         : 0.3
Green Y                         : 0.6
Blue X                          : 0.15
Blue Y                          : 0.06
Background Color                : 255 255 255
XMP Toolkit                     : Image::ExifTool 11.88
Creator                         : Javier Turcot
Image Size                      : 400x300
Megapixels                      : 0.120
```
#### Final: 
The Creators full name is Javier Turcot. Format now the creators name to `firstname_lastname` -> `javier_turcot` and that is the flag. 

### Terminal Logs
```Ubuntu
x47@LAPTOP-J6FFFBS9:~$ gunzip ch39.gz
x47@LAPTOP-J6FFFBS9:~$ tar -xvf ch39
usb.image
x47@LAPTOP-J6FFFBS9:~$ file usb.image
usb.image: DOS/MBR boot sector, code offset 0x3c+2, OEM-ID "mkfs.fat", sectors/cluster 4, reserved sectors 4, root entries 512, sectors 63488 (volumes <=32 MB), Media descriptor 0xf8, sectors/FAT 64, sectors/track 62, heads 124, hidden sectors 2048, reserved 0x1, serial number 0xc7ecde5b, label: "USB        ", FAT (16 bit)
x47@LAPTOP-J6FFFBS9:~$ fls -r usb.image
r/r 3:  USB         (Volume Label Entry)
r/r * 5:        anonyme.png
v/v 1013699:    $MBR
v/v 1013700:    $FAT1
v/v 1013701:    $FAT2
V/V 1013702:    $OrphanFiles
x47@LAPTOP-J6FFFBS9:~$ fls -d -p usb.image
r/r * 5:        anonyme.png
x47@LAPTOP-J6FFFBS9:~$ icat usb.image 5 > ch39-anonyme.png
x47@LAPTOP-J6FFFBS9:~$ exiftool ch39-anonyme.png
ExifTool Version Number         : 12.40
File Name                       : ch39-anonyme.png
Directory                       : .
File Size                       : 240 KiB
File Modification Date/Time     : 2023:09:11 11:56:28+02:00
File Access Date/Time           : 2023:09:11 11:56:28+02:00
File Inode Change Date/Time     : 2023:09:11 11:56:28+02:00
File Permissions                : -rw-r--r--
File Type                       : PNG
File Type Extension             : png
MIME Type                       : image/png
Image Width                     : 400
Image Height                    : 300
Bit Depth                       : 8
Color Type                      : RGB
Compression                     : Deflate/Inflate
Filter                          : Adaptive
Interlace                       : Noninterlaced
Gamma                           : 2.2
White Point X                   : 0.3127
White Point Y                   : 0.329
Red X                           : 0.64
Red Y                           : 0.33
Green X                         : 0.3
Green Y                         : 0.6
Blue X                          : 0.15
Blue Y                          : 0.06
Background Color                : 255 255 255
XMP Toolkit                     : Image::ExifTool 11.88
Creator                         : Javier Turcot
Image Size                      : 400x300
Megapixels                      : 0.120

```
