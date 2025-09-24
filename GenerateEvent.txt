@echo off
cd /d "<path to folder>"

REM American League teams (.EVA)
set AL_TEAMS=BAL BOS CHA CLE DET HOU KCA ANA MIN NYA OAK SEA TEX TOR TBA

REM National League teams (.EVN)
set NL_TEAMS=ARI ATL CHN CIN COL LAN MIA MIL NYN PHI PIT SDN SFN SLN WAS

for %%Y in (2022 2023 2024) do (

  REM AL files use .EVA
  for %%T in (%AL_TEAMS%) do (
    echo Processing %%Y%%T.EVA ...
    BEVENT -y %%Y -f 0,1,3,2,4,26,27,28,10,29,85,86 %%Y%%T.EVA > %%T%%Y.csv
  )

  REM NL files use .EVN
  for %%T in (%NL_TEAMS%) do (
    echo Processing %%Y%%T.EVN ...
    BEVENT -y %%Y -f 0,1,3,2,4,26,27,28,10,29,85,86 %%Y%%T.EVN > %%T%%Y.csv
  )

)

echo All done!
pause
