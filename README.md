# Stop the Steal / J6 profiles

This repository contains 9,736,593 user profile snapshots for (approximately)
ten thousand of the Twitter accounts that were most active in spreading false claims about
voter fraud in the months around the 2020 U.S. presidential election.

## Sources

The accounts were selected by taking the top ten thousand Twitter user IDs from the
"promoter" community in the [VoterFraud2020][voterfraud2020] dataset published by the
[Jacobs Technion-Cornell Institute](https://tech.cornell.edu/jacobs-technion-cornell-institute/)
at Cornell Tech.

We scraped tweet data for October 2020 through January 2021 from the [Twitter Stream Grab][twitter-stream-grab],
which is
published by the [Archive Team](https://archive.org/details/archiveteam) and the
[Internet Archive](https://archive.org/). From this data we extracted all user profiles for
accounts with our selected IDs, which results in 9,964 accounts being represented
(see [this document](https://gist.github.com/travisbrown/2e3da217335ed0cb492bb7720bbdae67)
for screen names for the 36 missing accounts).

While the VoterFraud2020 data is anonymized (only Twitter's user IDs are provided, not screen names
or other user information), this dataset is not. All public profile data is included here, including
bios, locations, and links, regardless of account status (39.7% of these accounts have been permanently suspended
by Twitter, and 11.7% have been deactivated by the account owner).

The additional data provided here allows us to track how accounts involved in these efforts
gained prominence over time, how they promoted events and hashtags in their bios and display names,
how they encouraged the use of alternative platforms such as Parler, Gab, and Telegram, etc.

Please note that all of this data was sourced from the Internet Archive and not directly from Twitter.

## Coverage

The coverage varies widely depending on the prominence of the account. There are
883,034 profile snapshots here for `@realDonaldTrump`, for example, while 42 accounts
have only a single profile snapshot. The median number of snapshots for an account is
124, which is about one per day.

There are gaps in the Archive Team data, which means there are gaps in our profile snapshots.
Two days in November are entirely missing, for example, and nineteen days in the middle of January.

## Format

The data is provided in the [JSON Lines](https://jsonlines.org/) format, with each user having their
own file in the `data` directory. The file name is the user's Twitter ID, with `jsonl` as the extension.
Please see the Twitter API documentation for [user objects](https://developer.twitter.com/en/docs/twitter-api/v1/data-dictionary/object-model/user)
for details about the JSON schema.

Each line in the file represents a single profile snapshot, but only includes fields that have changed
since the last snapshot. The first line is always a full user object, but each subsequent line will
generally contain a smaller number of fields.

For example, near the top of `data/1057379667890495488.jsonl` you'll find these lines:

```json
{"ts":"2020-10-02 21:51:50","favourites_count":5917,"followers_count":10540,"statuses_count":15514}
{"ts":"2020-10-03 01:50:30","followers_count":10541,"friends_count":8454,"statuses_count":15513}
{"ts":"2020-10-03 14:22:38","favourites_count":5915,"followers_count":10545,"friends_count":8455,"statuses_count":15518}
{"ts":"2020-10-04 05:52:48","favourites_count":5927,"followers_count":10546,"friends_count":8458,"screen_name":"MagaManAnon","statuses_count":15543}
```

The first three lines indicate changing numbers of followers, favorites, tweets, etc.
The fourth line also indicates that the user changed their screen name, from `@Dave64012590` (which we can find in the first line of the file)
to `@MagaManAnon`.

Note that the `ts` field at the beginning of each line is not part of the Twitter user object, but is a timestamp that
is added during our processing to indicate the time of the profile snapshot (we collect these values from the enclosing
status objects in the Archive Team source files during scraping). Times are UTC.

## Top 500 accounts

The table below contains links to the data files for the top 500 accounts
(according to the normalized closeness centrality values in the VoterFraud2020 dataset).

|Twitter ID|Status|Followers|Screen names|
|-|-|-|-|
|[25073877](data/25073877.jsonl)|suspended||realDonaldTrump|
|[187680645](data/187680645.jsonl)|suspended||LLinWood|
|[770781940341288960](data/770781940341288960.jsonl)|verified|1,137,346|RudyGiuliani, xxxxxxx37583982|
|[26487169](data/26487169.jsonl)|verified|2,144,540|LouDobbs, loudobbsnews|
|[4041824789](data/4041824789.jsonl)|verified|618,434|RSBNetwork|
|[240454812](data/240454812.jsonl)|suspended||GenFlynn|
|[586707638](data/586707638.jsonl)|suspended||SidneyPowell1|
|[2853461537](data/2853461537.jsonl)|verified|656,713|ScottAdamsSays|
|[16989178](data/16989178.jsonl)|suspended||JamesOKeefeIII|
|[18266688](data/18266688.jsonl)|verified|1,164,228|TomFitton|
|[321954654](data/321954654.jsonl)|verified|198,506|kylenabecker, IJReviewEditor, ijrviraleditor|
|[620571475](data/620571475.jsonl)|verified|1,436,057|DanScavino|
|[341194704](data/341194704.jsonl)|verified|91,431|SteveGuest|
|[19211550](data/19211550.jsonl)|suspended||gatewaypundit|
|[39344374](data/39344374.jsonl)|verified|7,100,658|DonaldJTrumpJr|
|[3932768472](data/3932768472.jsonl)|verified|436,688|EmeraldRobinson|
|[592730371](data/592730371.jsonl)|verified|1,473,197|JackPosobiec, AngryGoTFan|
|[3530404094](data/3530404094.jsonl)|active|612,512|DavidJHarrisJr|
|[302446244](data/302446244.jsonl)|active|13,582|txelectionlaw|
|[729676086632656900](data/729676086632656900.jsonl)|suspended||TeamTrump|
|[264501955](data/264501955.jsonl)|suspended||MichaelCoudrey, MikeTokes|
|[78523300](data/78523300.jsonl)|verified|2,424,068|RealJamesWoods|
|[45676731](data/45676731.jsonl)|verified|221,973|TimMurtaugh|
|[778763106289758208](data/778763106289758208.jsonl)|verified|899,629|JennaEllisEsq, JennaEllisJDFI, JennaEllisRives, JennaEllisorg, realJennaEllis|
|[29458079](data/29458079.jsonl)|verified|2,409,414|JudgeJeanine|
|[31457007](data/31457007.jsonl)|verified|6,731|chefjclark|
|[1196441152486072320](data/1196441152486072320.jsonl)|verified|406,061|CBS_Herridge|
|[826065164504006657](data/826065164504006657.jsonl)|verified|452,172|mtgreenee|
|[103744112](data/103744112.jsonl)|verified|6,528|aricnesbitt|
|[6782762](data/6782762.jsonl)|suspended||ali|
|[25837289](data/25837289.jsonl)|verified|268,186|BernardKerik|
|[1029094268542099457](data/1029094268542099457.jsonl)|verified|115,643|Lancegooden|
|[24127811](data/24127811.jsonl)|verified|212,677|mtracey|
|[1812055789](data/1812055789.jsonl)|suspended||CodeMonkeyZ|
|[720843893441306624](data/720843893441306624.jsonl)|verified|64,042|WomenforTrump|
|[292929271](data/292929271.jsonl)|verified|1,708,262|charliekirk11|
|[90480218](data/90480218.jsonl)|verified|614,098|RichardGrenell|
|[29097819](data/29097819.jsonl)|verified|430,664|EpochTimes|
|[3016071993](data/3016071993.jsonl)|verified|27,023|LifeZette|
|[963480595](data/963480595.jsonl)|verified|918,675|MarkMeadows, RepMarkMeadows|
|[19553409](data/19553409.jsonl)|verified|353,570|Rasmussen_Poll|
|[22055226](data/22055226.jsonl)|verified|409,762|replouiegohmert|
|[47739450](data/47739450.jsonl)|verified|435,165|ByronYork|
|[91882544](data/91882544.jsonl)|verified|1,822,526|DineshDSouza|
|[1290635110149169152](data/1290635110149169152.jsonl)|active|223,614|ElectionWiz, ConLawSays, ConLawScholar, HotTakesSays, LawScholarSays, LeallySpeaking, RogueEsq, SophistSays, Wizard_Predicts|
|[1108472017144201216](data/1108472017144201216.jsonl)|verified|1,305,169|TrumpWarRoom|
|[757832485](data/757832485.jsonl)|active|221,986|realLizUSA, LizRNC, LizWFB|
|[166751745](data/166751745.jsonl)|verified|940,276|RyanAFournier|
|[17582355](data/17582355.jsonl)|verified|112,905|DanPatrick|
|[875856268056969216](data/875856268056969216.jsonl)|suspended||DC_Draino|
|[39349894](data/39349894.jsonl)|verified|4,095,350|EricTrump|
|[3310061541](data/3310061541.jsonl)|verified|111,294|thejtlewis|
|[131546062](data/131546062.jsonl)|verified|361,738|SenRickScott, FLGovScott|
|[52338305](data/52338305.jsonl)|locked|502,525|BrandonStraka, Brandonstraka, usminority|
|[359403242](data/359403242.jsonl)|verified|169,148|kelliwardaz|
|[339984356](data/339984356.jsonl)|active|50,011|IvanPentchoukov|
|[15976697](data/15976697.jsonl)|verified|2,039,120|michellemalkin|
|[2975091705](data/2975091705.jsonl)|verified|88,956|CongressmanHice|
|[25202268](data/25202268.jsonl)|verified|1,288,551|SaraCarterDC|
|[83932539](data/83932539.jsonl)|suspended||prayingmedic|
|[2417586104](data/2417586104.jsonl)|verified|1,139,142|SebGorka|
|[18604137](data/18604137.jsonl)|verified|153,092|RonColeman|
|[24822993](data/24822993.jsonl)|suspended||tracybeanz|
|[1237612672373248000](data/1237612672373248000.jsonl)|active|145,998|Rothbard1776, Hoopsfan1776, Michael19315861|
|[259001548](data/259001548.jsonl)|verified|2,165,226|kayleighmcenany|
|[138809881](data/138809881.jsonl)|verified|294,367|mschlapp|
|[794652195484565504](data/794652195484565504.jsonl)|active|24,168|correctthemedia|
|[364214133](data/364214133.jsonl)|suspended||va_shiva|
|[6742412](data/6742412.jsonl)|verified|86,446|jennybethm|
|[201066140](data/201066140.jsonl)|verified|269,302|pnjaban|
|[149269179](data/149269179.jsonl)|verified|28,177|NVGOP|
|[850036892](data/850036892.jsonl)|suspended||Project_Veritas|
|[963297229](data/963297229.jsonl)|suspended||realTrumpForce|
|[2301990517](data/2301990517.jsonl)|active|210,248|barnes_law, Barnes_Law|
|[3406938525](data/3406938525.jsonl)|active|254,987|thebradfordfile, jbwredsox|
|[1242146812309405708](data/1242146812309405708.jsonl)|active|23,496|PandaTribune|
|[125128723](data/125128723.jsonl)|verified|368,196|RaheemKassam, RaheemJKassam|
|[18379614](data/18379614.jsonl)|verified|1,022,127|RubinReport|
|[15212187](data/15212187.jsonl)|verified|409,236|bennyjohnson|
|[3981225735](data/3981225735.jsonl)|verified|251,582|TrumpStudents|
|[27995424](data/27995424.jsonl)|verified|272,947|johncardillo|
|[2922345639](data/2922345639.jsonl)|suspended||DonnaWR8|
|[149681153](data/149681153.jsonl)|active|83,099|jbinnall|
|[406290234](data/406290234.jsonl)|suspended||Raiklin, raiklin|
|[1336828763108237313](data/1336828763108237313.jsonl)|active|5,259|SenWilliamLigon|
|[37575922](data/37575922.jsonl)|active|108,404|hollandcourtney|
|[14559721](data/14559721.jsonl)|verified|86,800|stinchfield1776|
|[16523905](data/16523905.jsonl)|verified|205,132|robbystarbuck|
|[18005085](data/18005085.jsonl)|verified|686,103|MZHemingway|
|[36529101](data/36529101.jsonl)|verified|319,660|seanmdav|
|[12008602](data/12008602.jsonl)|verified|28,236|carriesheffield|
|[872148729184362497](data/872148729184362497.jsonl)|verified|130,997|DrPaulGosar|
|[15937190](data/15937190.jsonl)|verified|121,077|AZGOP|
|[27000730](data/27000730.jsonl)|verified|902,370|Timcast|
|[21722318](data/21722318.jsonl)|active|190,719|willchamberlain|
|[2778328297](data/2778328297.jsonl)|suspended||MajorP8riot, MajorPatriot, Q2dWave, Q2ndWave, Q_2ndWave|
|[601535938](data/601535938.jsonl)|active|527,977|RealMattCouch|
|[762389795037294592](data/762389795037294592.jsonl)|active|479,902|TheRightMelissa, sweetatertot2, sweetweetertot, sweetweetertot2|
|[1170886272](data/1170886272.jsonl)|verified|44,930|AdamLaxalt|
|[129571843](data/129571843.jsonl)|verified|116,628|RealKyleMorris|
|[16834659](data/16834659.jsonl)|verified|569,410|SkyNewsAust|
|[235839823](data/235839823.jsonl)|verified|522,993|HerschelWalker|
|[877985300466745344](data/877985300466745344.jsonl)|active|426,837|JosephJFlynn1|
|[3047722897](data/3047722897.jsonl)|suspended||realMikeLindell|
|[38495835](data/38495835.jsonl)|verified|2,623,632|marklevinshow|
|[375721095](data/375721095.jsonl)|active|916,155|Breaking911, Breaking9ll, breaking9111|
|[44385628](data/44385628.jsonl)|verified|395,423|gregkellyusa|
|[772934961766608897](data/772934961766608897.jsonl)|active|53,196|NatalieJHarp, nataliejharp|
|[172511244](data/172511244.jsonl)|verified|104,932|T_S_P_O_O_K_Y|
|[18089606](data/18089606.jsonl)|verified|371,193|KurtSchlichter|
|[25386925](data/25386925.jsonl)|active|30,168|KylieJaneKremer|
|[18822612](data/18822612.jsonl)|verified|85,967|AmyKremer|
|[4765364386](data/4765364386.jsonl)|verified|275,650|ChuckCallesto|
|[523248016](data/523248016.jsonl)|active|856,908|jsolomonReports|
|[90651198](data/90651198.jsonl)|verified|674,713|GregAbbott_TX|
|[19612749](data/19612749.jsonl)|active|24,228|EagleEdMartin|
|[237299871](data/237299871.jsonl)|verified|116,010|RepMoBrooks|
|[259260816](data/259260816.jsonl)|suspended||zeusFanHouse|
|[317385247](data/317385247.jsonl)|suspended||iheartmindy|
|[966612436978581504](data/966612436978581504.jsonl)|suspended||AOECOIN|
|[23317891](data/23317891.jsonl)|suspended||docdhj|
|[1304530918716190721](data/1304530918716190721.jsonl)|suspended||DatElefan, DatElefent, DataElefantFan, DeeElefans, DeeElefantMan, ElElephantes, ElefentGamer, ElefentJames, Elefentis, GamerElefent, GodofElephant, ManofElefants, MrElefantes, MrElefent, MrRedElephant, TheElefentGamer, YoDatElefant, YoDatElefent, YoDatSmellefant, YoElefant, the_elefent|
|[182524533](data/182524533.jsonl)|active|24,392|docMJP|
|[96502351](data/96502351.jsonl)|verified|217,647|WendyRogersAZ|
|[16124531](data/16124531.jsonl)|active|22,786|MalcolmOutLoud|
|[931286316](data/931286316.jsonl)|verified|860,790|ScottPresler|
|[1201670995435646976](data/1201670995435646976.jsonl)|verified|736,392|laurenboebert|
|[736989573201301504](data/736989573201301504.jsonl)|suspended||KelemenCari|
|[4798259061](data/4798259061.jsonl)|deactivated||BarbaraRedgate|
|[187022370](data/187022370.jsonl)|suspended||steven_l_cox|
|[1901916354](data/1901916354.jsonl)|verified|23,248|MattFinnFNC|
|[2908170952](data/2908170952.jsonl)|verified|1,320,693|DiamondandSilk|
|[19091173](data/19091173.jsonl)|verified|1,351,312|scrowder|
|[1010027784318488576](data/1010027784318488576.jsonl)|suspended||RoscoeBDavis1|
|[902200087](data/902200087.jsonl)|verified|264,651|CassandraRules|
|[21149655](data/21149655.jsonl)|verified|98,900|ArthurSchwartz, arthurschwartz|
|[358545917](data/358545917.jsonl)|verified|777,786|Cernovich, PlayDangerously|
|[1043185714437992449](data/1043185714437992449.jsonl)|active|588,134|catturd2|
|[448849326](data/448849326.jsonl)|suspended||AfghanTourist, TonyToez|
|[74303349](data/74303349.jsonl)|deactivated||MarkFinchem|
|[1209936918](data/1209936918.jsonl)|verified|1,483,471|OANN|
|[3056035526](data/3056035526.jsonl)|active|6,244|calebthom1, gopcaleb|
|[739610364975808513](data/739610364975808513.jsonl)|suspended||paulsperry_|
|[15719232](data/15719232.jsonl)|active|57,922|JanJekielek|
|[4165642155](data/4165642155.jsonl)|suspended||AMPIsa4031, AMPRo1219, CRRJA5, CaterpillarWins, Connie4USA, ConstanceQueen8, CorneredCRRJA5, ECHOtheCALL, GameOnPatriots, Isa4031AMP, NIVIsa4031, NIVPsalm8412, RealEagleWings, Rise1Soar2BFree, Rise_Soar_BFree, SoarOnTheWings, SocialismStench, Text88022|
|[532256587](data/532256587.jsonl)|deactivated||PeterJCrotser|
|[1139029234163245056](data/1139029234163245056.jsonl)|active|55,440|Brick_Suit|
|[17936949](data/17936949.jsonl)|suspended||KMCRadio|
|[165039823](data/165039823.jsonl)|active|170,869|Peoples_Pundit|
|[988573326376427520](data/988573326376427520.jsonl)|verified|2,955,554|SecPompeo|
|[2393323908](data/2393323908.jsonl)|verified|347,834|thecjpearson|
|[2353605901](data/2353605901.jsonl)|verified|979,456|GOPChairwoman|
|[233000889](data/233000889.jsonl)|verified|214,134|fleccas|
|[816652616625168388](data/816652616625168388.jsonl)|verified|347,454|RepAndyBiggsAZ|
|[719662077934243840](data/719662077934243840.jsonl)|suspended||Can2geterdone, cantgeterdone|
|[1084375028](data/1084375028.jsonl)|verified|366,315|JasonMillerinDC|
|[2996253413](data/2996253413.jsonl)|verified|365,583|RandyRRQuaid|
|[232901331](data/232901331.jsonl)|verified|2,397,097|dbongino|
|[69190453](data/69190453.jsonl)|suspended||LVNancy|
|[105901883](data/105901883.jsonl)|verified|127,775|ericmetaxas|
|[441724006](data/441724006.jsonl)|suspended||illuminateheros|
|[307039459](data/307039459.jsonl)|active|96,098|molmccann|
|[2852597261](data/2852597261.jsonl)|active|149,339|julie_kelly2|
|[878247600096509952](data/878247600096509952.jsonl)|verified|2,970,816|RealCandaceO, RedPillBlack|
|[466864852](data/466864852.jsonl)|active|258,927|BoSnerdley|
|[951302891708583936](data/951302891708583936.jsonl)|suspended||TheRISEofROD|
|[15777543](data/15777543.jsonl)|verified|20,453|zenxv|
|[4158758146](data/4158758146.jsonl)|suspended||GmanFan44, GmanFan45|
|[2713427480](data/2713427480.jsonl)|suspended||adjunctpr0fessr, adjunctprofesor, adjunctprofesr1, adjunctprofesr2, adjunctprofessr, adjunctprofeszr, adjunctprofezsr|
|[499154896](data/499154896.jsonl)|active|111,806|alexbruesewitz, alexanderbruz|
|[1242534200634478593](data/1242534200634478593.jsonl)|active|185,127|RealPNavarro, PeterNavarro45, WH45OTMP|
|[1015029427284127745](data/1015029427284127745.jsonl)|active|24,314|HizbkKhan|
|[18029328](data/18029328.jsonl)|verified|36,593|SecretsBedard|
|[237829375](data/237829375.jsonl)|active|17,794|ThyConsigliori|
|[774074669230071809](data/774074669230071809.jsonl)|active|34,388|VoteTrumpPics|
|[1324742403492892673](data/1324742403492892673.jsonl)|active|6,738|crabcrawler1|
|[49023129](data/49023129.jsonl)|suspended||cjtruth|
|[2438831503](data/2438831503.jsonl)|verified|443,665|ChanelRion|
|[3158234814](data/3158234814.jsonl)|active|42,902|thechrisbuskirk|
|[1197653491214368768](data/1197653491214368768.jsonl)|suspended||BestIsYet2Com, TrumpRulzz|
|[25871116](data/25871116.jsonl)|active|541|extickerpimp|
|[895954495116644352](data/895954495116644352.jsonl)|suspended||tom2badcat|
|[29495695](data/29495695.jsonl)|verified|189,890|KLoeffler, kloeffler|
|[764261361044037632](data/764261361044037632.jsonl)|suspended||dmills3710|
|[16597389](data/16597389.jsonl)|verified|86,332|bethanyshondark|
|[1074480192](data/1074480192.jsonl)|verified|2,271,999|SenTedCruz|
|[19149039](data/19149039.jsonl)|verified|53,181|DavidShafer|
|[34082620](data/34082620.jsonl)|verified|308,989|JesseKellyDC|
|[2916305152](data/2916305152.jsonl)|verified|5,008,846|Snowden|
|[19721592](data/19721592.jsonl)|verified|54,801|debostic|
|[20813198](data/20813198.jsonl)|verified|5,468|VictorJoecks|
|[15455253](data/15455253.jsonl)|verified|182,643|nedryun|
|[960285302899298304](data/960285302899298304.jsonl)|suspended||4uConservatives, EvanAKilgore|
|[50434933](data/50434933.jsonl)|active|224,970|LifeNewsHQ, StevenErtelt|
|[2835451658](data/2835451658.jsonl)|verified|897,057|MrAndyNgo|
|[1324434386062696448](data/1324434386062696448.jsonl)|suspended||StopTheStealUS|
|[18956073](data/18956073.jsonl)|verified|288,692|dcexaminer|
|[591505507](data/591505507.jsonl)|suspended||michaelbeatty3|
|[15392486](data/15392486.jsonl)|active|681,569|disclosetv|
|[2410068528](data/2410068528.jsonl)|suspended||aubrey_huff|
|[22677397](data/22677397.jsonl)|active|521,561|atensnut|
|[1209417007](data/1209417007.jsonl)|verified|473,010|SteveScalise|
|[1133781254959239168](data/1133781254959239168.jsonl)|verified|161,851|SenMastriano|
|[1216793092134723586](data/1216793092134723586.jsonl)|active|98,757|JustTheNews, JTNReports|
|[17364806](data/17364806.jsonl)|suspended||kimUSAStrong, kimfreethinker, kimusastrong, kjsm006|
|[1890308449](data/1890308449.jsonl)|verified|41,205|bhweingarten|
|[1325639866881863681](data/1325639866881863681.jsonl)|suspended||DrRajRamheel, MilionMagaMarch, WelrdStuff|
|[1110684264243302400](data/1110684264243302400.jsonl)|deactivated||GoJackFlynn, JackFly94274864|
|[624210678](data/624210678.jsonl)|verified|216,250|Millie__Weaver|
|[36912523](data/36912523.jsonl)|verified|3,158|RepDaveWilliams|
|[166414119](data/166414119.jsonl)|verified|15,866|elisa1121|
|[1858882886](data/1858882886.jsonl)|active|28,926|JMichaelWaller|
|[1324700371156111360](data/1324700371156111360.jsonl)|suspended||BeingRealMac, ImpossibleMac, TypeWriterMac, TypeWritersTwit|
|[22663306](data/22663306.jsonl)|active|70,690|my3monkees|
|[229141520](data/229141520.jsonl)|verified|263,923|CortesSteve|
|[1008598678523842560](data/1008598678523842560.jsonl)|suspended||culttture|
|[476848835](data/476848835.jsonl)|active|10,323|JustTheTweets17, Texastrue11|
|[216881337](data/216881337.jsonl)|verified|3,405,063|RandPaul, SenRandPaul|
|[94784682](data/94784682.jsonl)|active|221,858|JonathanTurley|
|[16912983](data/16912983.jsonl)|verified|24,297|jeffgiesea|
|[203226736](data/203226736.jsonl)|verified|336,427|SharylAttkisson|
|[528999980](data/528999980.jsonl)|suspended||RL9631|
|[991089617603411968](data/991089617603411968.jsonl)|suspended||JuliansRum, JuliansRumGlass|
|[1188713068877844480](data/1188713068877844480.jsonl)|suspended||erskineradio|
|[3267456386](data/3267456386.jsonl)|active|217,843|ColumbiaBugle|
|[2284041356](data/2284041356.jsonl)|suspended||themodalice|
|[534881613](data/534881613.jsonl)|verified|302,647|Annakhait|
|[1153042794375712770](data/1153042794375712770.jsonl)|active|71,103|HowleyReporter|
|[14828860](data/14828860.jsonl)|verified|207,258|michaeljohns|
|[16585101](data/16585101.jsonl)|suspended||ouMAGAgirl, ouchinagirl|
|[454513795](data/454513795.jsonl)|suspended||9NEWSNANCY, 9NewsNancy, ChooseToBFree, FIGHT_2_KAG, NANCY9NATION, NINENEWSNANCY, Nancys_News, NineNewsNancy|
|[18247062](data/18247062.jsonl)|verified|1,646,167|JudicialWatch|
|[334715818](data/334715818.jsonl)|verified|580,775|BuckSexton|
|[274891222](data/274891222.jsonl)|suspended||bfraser747, bfraser757|
|[20975060](data/20975060.jsonl)|verified|217,279|johnrobertsFox|
|[15669672](data/15669672.jsonl)|suspended||PamelaGeller|
|[20545835](data/20545835.jsonl)|verified|1,003,680|newsmax, Newsmax_Media|
|[832978972602429440](data/832978972602429440.jsonl)|verified|173,171|GrahamAllen_1|
|[393190233](data/393190233.jsonl)|suspended||LeahR77|
|[96906231](data/96906231.jsonl)|active|67,861|thevivafrei|
|[25086658](data/25086658.jsonl)|verified|32,433|congbillposey|
|[27067705](data/27067705.jsonl)|active|15,606|PhillyGOP|
|[2795404498](data/2795404498.jsonl)|suspended||PVeritas_Action|
|[14407458](data/14407458.jsonl)|active|20,080|mikeroman|
|[397526755](data/397526755.jsonl)|verified|60,398|aaronjcarpenter, Ajcarpenter0|
|[4121225056](data/4121225056.jsonl)|verified|515,903|CLewandowski_|
|[66923871](data/66923871.jsonl)|verified|91,010|PARISDENNARD|
|[63327519](data/63327519.jsonl)|suspended||Qtah17, QtahPatriot, jonricketts|
|[1060573081935249409](data/1060573081935249409.jsonl)|active|72,312|news_ntd|
|[1098091506886471680](data/1098091506886471680.jsonl)|verified|264,951|laralogan|
|[34241428](data/34241428.jsonl)|active|23,272|RichValdes, richvaldes|
|[30540789](data/30540789.jsonl)|active|173,535|montaga|
|[792096589191852033](data/792096589191852033.jsonl)|active|119,218|themarketswork|
|[722528529716383744](data/722528529716383744.jsonl)|verified|341,798|ACTBrigitte|
|[1167174850479316996](data/1167174850479316996.jsonl)|verified|7,964|DemandDanielAZ|
|[195271137](data/195271137.jsonl)|verified|979,671|larryelder|
|[1204822874848186369](data/1204822874848186369.jsonl)|suspended||JaromeBellVA|
|[812135885328236551](data/812135885328236551.jsonl)|verified|307,086|RealSaavedra|
|[877699334](data/877699334.jsonl)|suspended||Tombx7M|
|[1318701904524939264](data/1318701904524939264.jsonl)|suspended||RN4Trump2020, RN7JB|
|[93059852](data/93059852.jsonl)|active|112,212|LeeSmithDC, LeeSmithTWS|
|[2327400218](data/2327400218.jsonl)|active|61,827|C_3C_3, C_3C_3_, C_3MAGA, cml3MAGA|
|[939921079673479169](data/939921079673479169.jsonl)|suspended||ArmandKllein, XArmandKleinX|
|[921468286453321728](data/921468286453321728.jsonl)|suspended||JudgeJeaninefan|
|[23438548](data/23438548.jsonl)|suspended||wglady|
|[11622712](data/11622712.jsonl)|verified|103,536|JDRucker, 0boy|
|[829735580](data/829735580.jsonl)|suspended||Mike_Beacham|
|[800086706678419456](data/800086706678419456.jsonl)|suspended||1776Stonewall|
|[338473859](data/338473859.jsonl)|active|32,861|BrandonBeckham, BrandonBeckham_|
|[84797861](data/84797861.jsonl)|verified|9,443|Alec_Mazo|
|[958486680436117504](data/958486680436117504.jsonl)|suspended||kitchigiwah1|
|[177584156](data/177584156.jsonl)|verified|192,611|jjauthor|
|[594886554](data/594886554.jsonl)|active|164,518|TheLastRefuge2|
|[10292132](data/10292132.jsonl)|verified|183,721|joelpollak|
|[118567880](data/118567880.jsonl)|verified|154,812|davereaboi|
|[23022687](data/23022687.jsonl)|verified|4,599,030|tedcruz|
|[495379332](data/495379332.jsonl)|suspended||GKeile|
|[99994358](data/99994358.jsonl)|verified|60,283|RickyRebelRocks|
|[41063062](data/41063062.jsonl)|active|46,071|RobertPLewis|
|[23360808](data/23360808.jsonl)|suspended||yogagenie|
|[17349381](data/17349381.jsonl)|verified|159,729|frfrankpavone|
|[88426758](data/88426758.jsonl)|suspended||SJPFISH|
|[321190259](data/321190259.jsonl)|verified|64,456|LizWillis_, _LizWillis|
|[4171684919](data/4171684919.jsonl)|suspended||KarrieFleetwood|
|[179245596](data/179245596.jsonl)|active|292,655|DavidLimbaugh|
|[16106584](data/16106584.jsonl)|verified|286,081|stillgray|
|[1052225335318712320](data/1052225335318712320.jsonl)|suspended||annvandersteel|
|[143169070](data/143169070.jsonl)|verified|66,169|CarmineSabia|
|[1031747223569227776](data/1031747223569227776.jsonl)|active|99,848|DarrenJBeattie|
|[744070482832596992](data/744070482832596992.jsonl)|verified|103,436|joshdcaplan|
|[208155240](data/208155240.jsonl)|verified|932,617|MariaBartiromo|
|[115681686](data/115681686.jsonl)|active|94,824|NetworksManager|
|[3634508187](data/3634508187.jsonl)|active|154,092|jackmurphylive|
|[22815781](data/22815781.jsonl)|active|38,603|KHerriage|
|[20394822](data/20394822.jsonl)|active|34,264|mrddmia|
|[704943112217608193](data/704943112217608193.jsonl)|active|144,794|MattBraynard|
|[24471951](data/24471951.jsonl)|active|80,261|carolmswain|
|[1117898546055761920](data/1117898546055761920.jsonl)|verified|68,242|BarnettforAZ|
|[17993620](data/17993620.jsonl)|active|25,762|kenblackwell|
|[1141043467822481408](data/1141043467822481408.jsonl)|suspended||ReportBread|
|[879548970082721792](data/879548970082721792.jsonl)|active|94,025|rising_serpent|
|[1546656000](data/1546656000.jsonl)|suspended||Jali_Benz, Jali_Cat, shygal0000|
|[213513491](data/213513491.jsonl)|suspended||diana_west_|
|[14347972](data/14347972.jsonl)|verified|87,930|Heminator|
|[1628841380](data/1628841380.jsonl)|deactivated||AdrianaCohen16|
|[91583544](data/91583544.jsonl)|verified|208,016|NickAdamsinUSA|
|[597607476](data/597607476.jsonl)|suspended||DenverFlynn|
|[1330274087218851852](data/1330274087218851852.jsonl)|active|84,283|PhillDKline|
|[1390318944](data/1390318944.jsonl)|active|14,200|Defeat_Joe, Defend_Trump|
|[2471692340](data/2471692340.jsonl)|verified|192,181|PastorDScott|
|[39785748](data/39785748.jsonl)|deactivated||ddwiese|
|[1257117821793951746](data/1257117821793951746.jsonl)|suspended||Kimona68672915, KimonaQ|
|[975200486](data/975200486.jsonl)|verified|258,092|RepThomasMassie|
|[1887528152](data/1887528152.jsonl)|verified|52,632|Bruce_LeVell|
|[849111344116838400](data/849111344116838400.jsonl)|suspended||Truthteller1349|
|[47293791](data/47293791.jsonl)|verified|1,008,196|w_terrence|
|[1259714432](data/1259714432.jsonl)|verified|439,084|kimKBaltimore, KimKlacik|
|[1272319965199306752](data/1272319965199306752.jsonl)|suspended||HoosierMike8, IndianaMAGAMike|
|[32201297](data/32201297.jsonl)|verified|129,092|mirandadevine|
|[1213874306515554306](data/1213874306515554306.jsonl)|suspended||AwakenedOutlaw|
|[1319014056666288128](data/1319014056666288128.jsonl)|suspended||Captain33497226, CaptainKraken87, CaptainTrump87, ChumpCaptain|
|[1295339359865110528](data/1295339359865110528.jsonl)|deactivated||2020djt2020, djt12029471, real1Thomas|
|[983766825610694656](data/983766825610694656.jsonl)|verified|244,851|AndrewPollackFL|
|[122287198](data/122287198.jsonl)|active|6,764|orijonal|
|[34400375](data/34400375.jsonl)|verified|14,699|WUWMradio|
|[940409602155282432](data/940409602155282432.jsonl)|active|131,415|FogCityMidge, magamidge|
|[339217151](data/339217151.jsonl)|suspended||Deb4truth, Debbideedoodah|
|[218758933](data/218758933.jsonl)|active|5,836|thisLAJenn|
|[33908800](data/33908800.jsonl)|verified|151,052|kevincorke|
|[116384038](data/116384038.jsonl)|active|30,217|pepesgrandma|
|[1072342620024815622](data/1072342620024815622.jsonl)|active|38,281|LATAMforTRUMP, latxtrump|
|[4710708974](data/4710708974.jsonl)|active|68,166|christianllamar|
|[1002379414162640896](data/1002379414162640896.jsonl)|active|8,805|AJLovesUSA|
|[63525003](data/63525003.jsonl)|verified|47,000|YossiGestetner|
|[26900055](data/26900055.jsonl)|active|160,846|DrMartyFox|
|[38284349](data/38284349.jsonl)|suspended||RealWayneRoot, WayneRoot|
|[798945991386955776](data/798945991386955776.jsonl)|deactivated||JBryanEure|
|[20118767](data/20118767.jsonl)|verified|217,218|RealDrGina|
|[7702542](data/7702542.jsonl)|verified|1,102,877|DLoesch|
|[1079776144524754944](data/1079776144524754944.jsonl)|verified|698,162|NikkiHaley|
|[1298093598475395072](data/1298093598475395072.jsonl)|suspended||SGaeta88|
|[1293984914652762114](data/1293984914652762114.jsonl)|suspended||Godwins1234, Savingworld88|
|[1445111881](data/1445111881.jsonl)|suspended||AngelWarrior321|
|[1085225533623783424](data/1085225533623783424.jsonl)|suspended||KanekoaTheGreat, TravelerNikola, TravelingTesla|
|[875017115979403264](data/875017115979403264.jsonl)|suspended||LaylaAlisha11, LaylaBlock2|
|[934049237628841984](data/934049237628841984.jsonl)|active|77,942|AKA_RealDirty, MrDirtyTruth, MrX_U812|
|[220081296](data/220081296.jsonl)|verified|196,822|HeatherChilders|
|[850507814023942144](data/850507814023942144.jsonl)|verified|785,013|GeorgePapa19|
|[1270489357208649728](data/1270489357208649728.jsonl)|active|22,001|JosephFordCotto, CottoGottfried|
|[901063185305882624](data/901063185305882624.jsonl)|active|26,927|Nick_Clamorgan|
|[1192537046134534155](data/1192537046134534155.jsonl)|suspended||1216tor, Orcusa1, Usa1cap, Usa1tor, Usatorz1, zx101z|
|[33608041](data/33608041.jsonl)|verified|679,039|ksorbs|
|[1313966902704771072](data/1313966902704771072.jsonl)|active|28,617|BlueSky_Report|
|[1494835716](data/1494835716.jsonl)|active|101,884|AIIAmericanGirI|
|[72616616](data/72616616.jsonl)|active|2,652|Elisa_freedom, elisa_combs|
|[2596413645](data/2596413645.jsonl)|suspended||carrieksada, carrieksada1, carrieksada_|
|[1058187189740339201](data/1058187189740339201.jsonl)|suspended||AshleyWeis4|
|[1067003156838662144](data/1067003156838662144.jsonl)|suspended||FuctupMike|
|[2874102076](data/2874102076.jsonl)|active|388,573|stclairashley|
|[834678265](data/834678265.jsonl)|active|671|susanwho2|
|[1217558302797828098](data/1217558302797828098.jsonl)|suspended||anon_fa_mous, anony_fa_mous|
|[85498982](data/85498982.jsonl)|deactivated||RealEricCarmen|
|[25248934](data/25248934.jsonl)|active|3,445|davidboxenhorn|
|[204444440](data/204444440.jsonl)|active|97,549|SexCounseling|
|[1045558231](data/1045558231.jsonl)|suspended||VFL2013|
|[3353061012](data/3353061012.jsonl)|suspended||Jamierodr10, Jamierodr14|
|[3262160865](data/3262160865.jsonl)|active|11,157|HonorAndDaring|
|[1326712271628853249](data/1326712271628853249.jsonl)|suspended||donfather_the|
|[37862226](data/37862226.jsonl)|suspended||hppyjesusfreak|
|[830538315036229632](data/830538315036229632.jsonl)|suspended||Sundncefn|
|[1237578874424344576](data/1237578874424344576.jsonl)|active|21,226|crossroads_josh, crossro45309909|
|[1225779630](data/1225779630.jsonl)|deactivated||BeholdIsrael|
|[739863724694110208](data/739863724694110208.jsonl)|deactivated||FieldofFight, RealMFlynnJr|
|[45641358](data/45641358.jsonl)|suspended||PolitixGal|
|[1185568362870591488](data/1185568362870591488.jsonl)|suspended||DaphneeMoon7, MaybeAmes|
|[910003499546566658](data/910003499546566658.jsonl)|suspended||NoqReport|
|[15515169](data/15515169.jsonl)|verified|185,793|toddstarnes|
|[1110169090180743168](data/1110169090180743168.jsonl)|active|41|mandy7510|
|[236541422](data/236541422.jsonl)|verified|36,653|NanHayworth|
|[972162448949116928](data/972162448949116928.jsonl)|suspended||GymCoachMac, MaCQ9N, RedPillMaC|
|[365256150](data/365256150.jsonl)|suspended||JimTuscaloosaAl|
|[39308549](data/39308549.jsonl)|verified|823,202|DailyCaller|
|[1576268089](data/1576268089.jsonl)|verified|18,796|GiancarloSopo|
|[412833880](data/412833880.jsonl)|deactivated||RealDrBurry, elfstones, michaeljburry|
|[2352629311](data/2352629311.jsonl)|verified|685,789|HawleyMO|
|[633966700](data/633966700.jsonl)|verified|48,480|AlanaKStewart|
|[503169119](data/503169119.jsonl)|suspended||tbstewart_2|
|[15757578](data/15757578.jsonl)|verified|72,076|JimHansonDC, Uncle_Jimbo|
|[1159452002646134786](data/1159452002646134786.jsonl)|suspended||BMcCodeOvets125, JosephM54106054|
|[1344539976](data/1344539976.jsonl)|active|33,001|SpringSteps, CCSunnyDay|
|[1312481033619566594](data/1312481033619566594.jsonl)|suspended||thepatriotgirl1|
|[977081455556866048](data/977081455556866048.jsonl)|active|853|OlorunjeJ|
|[462104542](data/462104542.jsonl)|locked|547,438|chuckwoolery|
|[25101996](data/25101996.jsonl)|verified|1,786,954|kimguilfoyle|
|[816131319033950208](data/816131319033950208.jsonl)|verified|80,724|RepJimBanks|
|[3995778614](data/3995778614.jsonl)|verified|394,417|KamVTV|
|[1324314793075974145](data/1324314793075974145.jsonl)|suspended||BobFighter45|
|[1408003598](data/1408003598.jsonl)|verified|288,923|FDRLST|
|[56491860](data/56491860.jsonl)|suspended||DrNealHouston|
|[3383049855](data/3383049855.jsonl)|deactivated||CrazyAboutTrump, Kotcha301, KotchaTheGreat|
|[1848966620](data/1848966620.jsonl)|deactivated||HillForMissouri|
|[29229098](data/29229098.jsonl)|verified|2,255|Justin_Riemer|
|[91279573](data/91279573.jsonl)|verified|330,991|AdamBaldwin|
|[1312783798258536449](data/1312783798258536449.jsonl)|suspended||fighttofighting, mehdigorji8|
|[786736292809760769](data/786736292809760769.jsonl)|suspended||CSeesTruth, CTruthforTrump, DrunksDomEnemy, FreeIllinoisNow, cindyseestruth, cs001234sc, cs00582sc, cs00582scs, cs0058sc, cs0058sc11, cs0058sc2, csCindySees|
|[1037175323614429184](data/1037175323614429184.jsonl)|active|10,464|Eyconik|
|[813473555572670464](data/813473555572670464.jsonl)|active|4,995|whthfk1|
|[19782840](data/19782840.jsonl)|active|24,362|WestonMartinez|
|[2480268229](data/2480268229.jsonl)|active|578,166|TheOfficerTatum|
|[478855762](data/478855762.jsonl)|verified|226,571|JessieJaneDuff|
|[1886919373](data/1886919373.jsonl)|verified|4,253|HowardSteele5|
|[968475170](data/968475170.jsonl)|suspended||JJDallasTexas|
|[1092086942198452224](data/1092086942198452224.jsonl)|suspended||no_silenced|
|[395062598](data/395062598.jsonl)|active|70|ltbeach1|
|[899115298997055491](data/899115298997055491.jsonl)|suspended||Trey_VonDinkis|
|[27888421](data/27888421.jsonl)|active|6,299|wmahoney5, GaltCountry, JGaltCountry|
|[774089965458354176](data/774089965458354176.jsonl)|active|20,384|BigFish3000, BillAtkinson77|
|[492833134](data/492833134.jsonl)|active|188,478|mikandynothem|
|[1323198422023761927](data/1323198422023761927.jsonl)|suspended||Christi53438799|
|[1024775399736311808](data/1024775399736311808.jsonl)|suspended||GA_peach3102|
|[32804484](data/32804484.jsonl)|active|29,800|Bubblebathgirl|
|[1330933210646261766](data/1330933210646261766.jsonl)|deactivated||Arbeus2|
|[4279853725](data/4279853725.jsonl)|suspended||JPMediaBoss, RealCryptoBoss, realjpbook, realttdaily|
|[2443083780](data/2443083780.jsonl)|suspended||IanMolony|
|[56149176](data/56149176.jsonl)|verified|48,954|derekahunter|
|[1326203693142843393](data/1326203693142843393.jsonl)|suspended||3peacefulheart|
|[3015067823](data/3015067823.jsonl)|active|4,117|shylockh|
|[1329553031919267844](data/1329553031919267844.jsonl)|suspended||MrRudyGiuliani|
|[382474068](data/382474068.jsonl)|suspended||DrewOO7|
|[713589805](data/713589805.jsonl)|active|4,419|nyfinest1995|
|[37324587](data/37324587.jsonl)|active|12,430|NYGuy13|
|[369233630](data/369233630.jsonl)|suspended||KMars64, KatMaher64, KathleenMaher64|
|[15819609](data/15819609.jsonl)|verified|32,104|ramprasad_c|
|[883855148136763392](data/883855148136763392.jsonl)|active|29,206|unseen1_unseen|
|[18085903](data/18085903.jsonl)|active|18,410|brianoflondon|
|[902987823183040512](data/902987823183040512.jsonl)|active|12,676|MAGAindex|
|[23362152](data/23362152.jsonl)|active|22,910|DanNewsManBall|
|[475274420](data/475274420.jsonl)|suspended||Travelbug1955|
|[86177206](data/86177206.jsonl)|verified|192,799|TPPatriots|
|[63335631](data/63335631.jsonl)|verified|236,972|Joy_Villa|
|[347627434](data/347627434.jsonl)|active|352,360|LindaSuhler|
|[751552860303683584](data/751552860303683584.jsonl)|suspended||superyayadize|
|[526707382](data/526707382.jsonl)|suspended||DGPurser|
|[11454572](data/11454572.jsonl)|suspended||martingeddes|
|[53745076](data/53745076.jsonl)|suspended||pinkbiscuit, pinkk9lover|
|[36528126](data/36528126.jsonl)|verified|1,544,648|kirstiealley|
|[788552327846322176](data/788552327846322176.jsonl)|suspended||TomStark913|
|[41634520](data/41634520.jsonl)|verified|5,450,237|seanhannity|
|[22150224](data/22150224.jsonl)|suspended||mizdonna|
|[50082136](data/50082136.jsonl)|active|9,329|courrielche|
|[122838840](data/122838840.jsonl)|deactivated||scotthowie23|
|[1334013465632059392](data/1334013465632059392.jsonl)|locked|364|PaulJEscandon|
|[900021957424447488](data/900021957424447488.jsonl)|verified|384,107|RepVernonJones, VernonJonesUSA1|
|[1201953403099893760](data/1201953403099893760.jsonl)|verified|166,687|RonnyJacksonTX, RonnyJackson4TX|
|[1174153996363345921](data/1174153996363345921.jsonl)|verified|17,596|Santos4Congress|
|[89083397](data/89083397.jsonl)|active|56,217|JoshJPhilipp|
|[15485532](data/15485532.jsonl)|verified|22,105|johnhawkinsrwn|
|[1141352946623492100](data/1141352946623492100.jsonl)|suspended||Concealcarrygrl|
|[15576967](data/15576967.jsonl)|suspended||robjh1|
|[717627639159128064](data/717627639159128064.jsonl)|suspended||TheTrumpLady, TrumpLadyFran|
|[332590264](data/332590264.jsonl)|suspended||theangiestanton|
|[1324579241430798339](data/1324579241430798339.jsonl)|suspended||BrianTh37895972|
|[1260320164463009792](data/1260320164463009792.jsonl)|suspended||ChatChristi|
|[468646961](data/468646961.jsonl)|verified|1,673,806|TomiLahren|
|[478367964](data/478367964.jsonl)|active|35,324|tom_trotts|
|[1138396700](data/1138396700.jsonl)|active|30,630|MythinformedMKE, MythicistMKE|
|[83748727](data/83748727.jsonl)|locked|104,253|FaithGoldy|
|[466809775](data/466809775.jsonl)|active|1,593|ValRichardson17|
|[1182332284403376128](data/1182332284403376128.jsonl)|active|67,338|TheFirstonTV|
|[125815552](data/125815552.jsonl)|suspended||AshlandFood, EinsteinMaga, EinsteinsMagic, Pepenstein|
|[2715055093](data/2715055093.jsonl)|suspended||JLMarchese111|
|[1299898009149472769](data/1299898009149472769.jsonl)|active|778|mermazingnik|
|[1334129399541673986](data/1334129399541673986.jsonl)|suspended||TheStealMovie|
|[1270521971848118272](data/1270521971848118272.jsonl)|active|33,654|PATPmovie|
|[2485417855](data/2485417855.jsonl)|verified|20,738|johnddavidson|
|[1687460006](data/1687460006.jsonl)|verified|44,292|MatthewTyrmand|
|[1677075974](data/1677075974.jsonl)|active|2,195|bradj_TX, b_rizzle03|
|[2899459274](data/2899459274.jsonl)|suspended||pam__sands, pam_sands|
|[1083125649609506816](data/1083125649609506816.jsonl)|verified|32,329|RepGregSteube|
|[1151484481603297280](data/1151484481603297280.jsonl)|deactivated||RichHiggins_DC|
|[624306656](data/624306656.jsonl)|active|25,210|D_Alex_connect|
|[33529092](data/33529092.jsonl)|active|164,284|SandraSentinel, SandraALTX, SandraAlabama, SandraTXAL, SandraTXAS|
|[2981776113](data/2981776113.jsonl)|active|25,531|blaze0497|
|[86374592](data/86374592.jsonl)|active|15,338|ReaganBabe, Reagan_Baby|
|[466789572](data/466789572.jsonl)|suspended||MissILmom|
|[1187652746](data/1187652746.jsonl)|verified|31,496|EmilyRoseFinn|
|[385568181](data/385568181.jsonl)|active|4,241|Eric_Cochran|
|[4778739981](data/4778739981.jsonl)|active|5,037|PALE_Primate, Pale_Primate|
|[1316035336712130560](data/1316035336712130560.jsonl)|suspended||Jashobeam17|
|[1230961593451712513](data/1230961593451712513.jsonl)|suspended||All50News, WeTheInevitable|
|[1324166009847123968](data/1324166009847123968.jsonl)|suspended||a68790304|
|[1309889774778540035](data/1309889774778540035.jsonl)|active|10,411|MericaNowNews, SaladinoShow, TheBasedGrandma|
|[583456963](data/583456963.jsonl)|deactivated||LATiffani1|
|[33417701](data/33417701.jsonl)|suspended||ScottFishman|
|[2857780588](data/2857780588.jsonl)|active|10,255|MintChipMusic, BasketOfSexy, MintChipMC|
|[324236072](data/324236072.jsonl)|verified|273,183|ObamaMalik|
|[393469195](data/393469195.jsonl)|verified|303,832|redsteeze|
|[2869844438](data/2869844438.jsonl)|suspended||nascarred14|
|[1242539267169157127](data/1242539267169157127.jsonl)|suspended||anonpatriotq|
|[1212764034388250626](data/1212764034388250626.jsonl)|active|1,485|KRHogan_NTD|

[twitter-stream-grab]: https://archive.org/details/twitterstream
[voterfraud2020]: https://github.com/sTechLab/VoterFraud2020

