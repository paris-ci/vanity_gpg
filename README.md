vanity_gpg
==========

Threaded vanity gpg key editor! Just choose your regex strings, it will generate keys until it finds a match, then save it!



usage:

    Edit vanitygen.pl, 
    choose your desired key_len, key_name, key_pass, key_email and thread_count(1 per logical core will typically saturate)
    
    choose your desired @needles - these will be parsed as independent regexes on your key (if you wish to match on short key, change the matching in keyThread ie: @matches= ($long_id -> @matches= ($short_id
    
    on an 8 core e5 Xeon it is roughly 5 2048 bit RSA keys/s
    
    Once a key is found, a <key_id>.sec.gpg, and <key_id>.pub.gpg will be generated in the working folder - you can remove any other extraneous .sec and .pub files created during the process (one per thread).
    
    Based off of Mayeu (https://gist.github.com/Mayeu/8575504)'s "Dirty Dirty Dirty" implementation.
    
    


Sample output:

# ./vanitygpg.pl

[...]
Found 169 keys so far, running for 29.5s (Rate:5.7/s)
Found S:1879B62A, L:9EE770521879B62A
Found S:BF9905B2, L:F0C32BCABF9905B2
Found S:1DD1EE38, L:41527DCC1DD1EE38
Found S:16B48D1C, L:CA13B46816B48D1C
Found S:D239C7C5, L:1A987705D239C7C5
Found S:F3257BBC, L:6550B451F3257BBC
Found S:C0C2045C, L:3AA5E481C0C2045C
Found S:7A1E3EEF, L:EED532257A1E3EEF
Found S:9646A225, L:8E69AD5B9646A225
Found S:58AB7AE0, L:4BE892EC58AB7AE0
Found S:057A877C, L:30DBB0B2057A877C
Found S:F51D72E8, L:5EA09842F51D72E8
Found S:29DA4CD4, L:1CE685F929DA4CD4
$VAR1 = '1CE';
Export 29DA4CD4
Found S:6C5334C6, L:AC1B0B2C6C5334C6
------ FOUND A KEY!!!!!!! ------

# ls *.gpg*
0x1CE685F929DA4CD4.pub.gpg  0x1CE685F929DA4CD4.sec.gpg
