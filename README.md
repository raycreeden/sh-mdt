# sh-mdt
Tablet policial sumamente completa, pero sin mapa en tiempo real en el dispatch
# 1-  para la instalacion de la mdt, lamentablemente al  no ser un job si no una integracion para qb-policejob deberan modificar un par de cosas minimas para que funcione correctamente en 

# 2-  entrar en Qb-policejob - Client - evidence.lua y agregar estas 2 lineas de codigo - solo son relevantes estas 2 lineas todo lo demas es un ejemplo para ubicarlo en el codigo
- local DISABLE_QB_EVIDENCE = true
- if not DISABLE_QB_EVIDENCE then
# dentro del codigo quedaria asi - no es necesario que pongas eso solo es como quedan ubicadas dentro del codigo 
-- Variables
local DISABLE_QB_EVIDENCE = true
local CurrentStatusList = {}
local Casings = {}
local CurrentCasing = nil
local Blooddrops = {}
local CurrentBlooddrop = nil
local Fingerprints = {}
local CurrentFingerprint = 0
local shotAmount = 0

if not DISABLE_QB_EVIDENCE then


local StatusList = {
    ['fight'] = Lang:t('evidence.red_hands'),
    ['widepupils'] = Lang:t('evidence.wide_pupils'),
    ['redeyes'] = Lang:t('evidence.red_eyes'),
    ['weedsmell'] = Lang:t('evidence.weed_smell'),
    ['gunpowder'] = Lang:t('evidence.gunpowder'),
    ['chemicals'] = Lang:t('evidence.chemicals'),
    ['heavybreath'] = Lang:t('evidence.heavy_breathing'),
    ['sweat'] = Lang:t('evidence.sweat'),
    ['handbleed'] = Lang:t('evidence.handbleed'),
    ['confused'] = Lang:t('evidence.confused'),
    ['alcohol'] = Lang:t('evidence.alcohol'),
    ['heavyalcohol'] = Lang:t('evidence.heavy_alcohol'),
    ['agitated'] = Lang:t('evidence.agitated')
}


# 3- Nuevamente en Qb-policejob - Client - main . en esta ocacion es el archivo de main.lua dentro del client  solo deberan comentar o eliminar, recomiendo solo comentar estas lineas .  no copien ni peguen nada las lineas de codigo son para mejor comprension para instalarlo.

-- RegisterNetEvent('police:client:policeAlert', function(coords, text)
--     local street1, street2 = GetStreetNameAtCoord(coords.x, coords.y, coords.z)
--     local street1name = GetStreetNameFromHashKey(street1)
--     local street2name = GetStreetNameFromHashKey(street2)
--     QBCore.Functions.Notify({ text = text, caption = street1name .. ' ' .. street2name }, 'police')
--     PlaySound(-1, 'Lose_1st', 'GTAO_FM_Events_Soundset', 0, 0, 1)
--     local transG = 250
--     local blip = AddBlipForCoord(coords.x, coords.y, coords.z)
--     local blip2 = AddBlipForCoord(coords.x, coords.y, coords.z)
--     local blipText = Lang:t('info.blip_text', { value = text })
--     SetBlipSprite(blip, 60)
--     SetBlipSprite(blip2, 161)
--     SetBlipColour(blip, 1)
--     SetBlipColour(blip2, 1)
--     SetBlipDisplay(blip, 4)
--     SetBlipDisplay(blip2, 8)
--     SetBlipAlpha(blip, transG)
--     SetBlipAlpha(blip2, transG)
--     SetBlipScale(blip, 0.8)
--     SetBlipScale(blip2, 2.0)
--     SetBlipAsShortRange(blip, false)
--     SetBlipAsShortRange(blip2, false)
--     PulseBlip(blip2)
--     BeginTextCommandSetBlipName('STRING')
--     AddTextComponentSubstringPlayerName(blipText)
--     EndTextCommandSetBlipName(blip)
--     while transG ~= 0 do
--         Wait(180 * 4)
--         transG = transG - 1
--         SetBlipAlpha(blip, transG)
--         SetBlipAlpha(blip2, transG)
--         if transG == 0 then
--             RemoveBlip(blip)
--             return
--         end
--     end
-- end)

 # 4 - Poner esto en qb-core items abajo de todo 
      tablet2                      = { name = 'tablet2', label = 'Tablet2', weight = 2000, type = 'item', image = 'tablet.png', unique = false, useable = false, shouldClose = true, description = 'Tablet Policial' },
    pol_camera                   = { name = 'pol_camera', label = 'Camara Policial', weight = 0, type = 'item', image = 'kinon.png', unique = true, useable = true, shouldClose = false, combinable = nil, description = 'Una Camara Tomar fotos de las Evidencias de una escena policial' },
    fotos_pol                    = { name = 'fotos_pol', label = 'Foto', weight = 0, type = 'item', image = 'fotos.png', unique = true, useable = true, shouldClose = false, combinable = nil, description = 'Una imagen'},
    infopol_evid                 = { name = 'infopol_evid', label = 'Informe Pol', weight = 0, type = 'item', image = 'infopol.png', unique = true, useable = true, shouldClose = false, combinable = nil, description = 'Documento de Evidencias'},
    pol_detector                 = { name = 'pol_detector', label = 'Detector de Estados', weight = 0, type = 'item', image = 'detector.png', unique = true, useable = true, shouldClose = false, combinable = nil, description = 'Detector de Estupefacientes' },

- La tablet no es usable, pero es requerida para que funcione  mediante la tecla,  y  esa imagen .png de la tablet ya viene por defecto en qb-core en su inventario
 
 # 5 - Ensurar pprimero " sh-radio" luego " sh-mdt" 
