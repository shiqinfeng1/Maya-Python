# Maya-Python
#Maya - Python Tools Developements

#Shader Attrib Modifier.py
mapTick = []
valueTick = []
allMats = cmds.ls(materials= True)
selMats = cmds.ls(selection = True)
gm = 0
# button Commands
Gatrrbs = ['cl']
# Color Values to K,G,M
cValue = [1.56, 1.65, 1.85]
k = cValue[0]
g = cValue[1]
m = cValue[2]
# input Custom attributs
damV = []
damM = []
def inputVal():
    global damV
    damV = cmds.textField('VField', text=True,query = True)
    return damV
    print damV
def inputMap():
    global damM
    damM = cmds.textField('MField', text=True,query = True)
    return damM
    print damM
class disCommands(object):
    def __init__(self):
        print  'Jay Sri Krishna'
        
    def disconRandom(self,am,froz):
        for i in am:
            textures = cmds.listConnections(i)
            for d in textures:
                try:
                    inputMap()
                    attrP = i + damM
                    attrA = d + '.outColor'
                    if froz:
                        cmds.editRenderLayerAdjustment(attrP)
                    cmds.disconnectAttr(attrA,attrP)
                except:
                    pass
                    
    def disOvridCommand(self,am,Count):
        for i in am:
            textures = cmds.listConnections(i)
            for d in textures:
                try:                    
                    attrC = i + cl
                    attrA = d + '.outColor'
                    if Count:
                        cmds.editRenderLayerAdjustment(attrC)
                    cmds.disconnectAttr(attrA,attrC)
                    hotspot.mapAttrbDiscon(damM)
                except:
                    pass
                    
    def colorWindow(self):
        global cValue
        result = cmds.colorEditor()
        buffer = result.split()
        if '1' == buffer[3]:
            cValue = cmds.colorEditor(query=True, rgb=True)
            print cValue
        else:
            print 'Editor was dismissed'
            
    def upDateV(self,am,Check):
        for ig in am:
            try:
                global k
                global g
                global m
                k = cValue[0]
                g = cValue[1]
                m = cValue[2]
                attrH = ig + cl
                if Check:
                    cmds.editRenderLayerAdjustment(attrH)
                cmds.setAttr(attrH, float(k), float(g), float(m), type = 'double3')
            except:
                print 'Wrong Values have been inserted'
            try:
                print inputVal()
                cmds.setAttr(attrH, float(damV))
            except:
                print 'Wrong Value Input'
                
    def attrUpdateV(self,am,shake):
        for ig in am:
            try:
                global k
                global g
                global m
                k = cValue[0]
                g = cValue[1]
                m = cValue[2]
                attrT = ig + damM
                if shake:
                    cmds.editRenderLayerAdjustment(attrT)
                cmds.setAttr(attrT, float(k), float(g), float(m), type = 'double3')
            except:
                try:
                    print inputVal()
                    cmds.setAttr(attrT, float(damV))
                except:
                    print 'Wrong Value Input in the box'
class BHoleCommand(object):
    def __init__(self):
        print ' Bharat mata ki Jay '
        
    def blackHole(self, Gate):
        for b in am:
            attrE = b +'.matteOpacityMode'
            attrF = b + '.matteOpacityMode'
            try:
                if Gate:
                    cmds.editRenderLayerAdjustment(attrE)
                cmds.setAttr( attrF, 0)
            except:
                pass
    
class chkAttrbDiscon(disCommands):
    def __init__(self):
        print 'Jai SriRam'
        hotspot.mapAttrbDiscon(cl)
        
    def attrbDiscon(self,cl):
        if int(gm) > 1:
            if len(mapTick) > 1:
                if len(am)>= 1:
                    self.disOvridCommand(am,1)
                else:
                    print 'check the Error'
            elif len(valueTick) > 1:
                if len(am)>= 1:
                    self.upDateV(am,1)
                else:
                    print 'Check the Error'
                    
        elif int(gm) == 0:
            if len(mapTick) > 1:
                if len(am)>= 1:
                    self.disOvridCommand(am,0)
                else:
                    print 'check the Error'
            elif len(valueTick) > 1:
                if len(am)>= 1:
                    self.upDateV(am,0)
                else:
                    print 'Check the Error'
        else:
            print 'page error'   
class chkMapAttrDiscon(disCommands):
    def __init__(self):
        print 'Indian superHero'
                            
    def mapAttrbDiscon(self,damM):
        if int(gm) > 1:
            if len(mapTick) > 1:
                if len(am)>= 1:
                    self.disconRandom(am,1)
                else:
                    print 'check the Error'
            elif len(valueTick) > 1:
                if len(am)>= 1:
                    self.attrUpdateV(am,1)
                else:
                    print 'Check the Error'
                    
        elif int(gm) == 0:
            if len(mapTick) > 1:
                if len(am)>= 1:
                    self.disconRandom(am,0)
                else:
                    print 'check the Error'
            elif len(valueTick) > 1:
                if len(am)>= 1:
                    self.attrUpdateV(am,0)
                else:
                    print 'Check the Error'
        else:
            print ' Page Error '
                    
class chkBlackHole(BHoleCommand):
    def __init__(self):
        print 'Jai Hind'
        
    def BattrbOvr(self):
        if int(gm) > 1:
            if len(am)>= 1:
                self.blackHole(1)    
            else:
                print 'Wrong Input Given'
        elif int(gm) == 0:
            if len(am)>= 1:
                self.blackHole(0)    
            else:
                print 'Wrong Input Given'
               
        else:
            print ' Page Black Error '
                
hotspot= chkMapAttrDiscon()
            
cmds.window( widthHeight=(260, 670), title="Global Attrb Modifier",bgc = (0.79,0.79,0.81) )
cmds.columnLayout( columnAttach=('both', 5), rowSpacing=20, columnWidth=250 )
cmds.rowColumnLayout( numberOfRows=1, cs = [(30, 40)]  )
cmds.checkBox( label='All', onc = 'am = allMats', ofc = 'am = 987'  )
cmds.checkBox( label='Selected', onc = 'am = cmds.ls(selection = True)', ofc = 'am = 987' )
cmds.setParent( '..' )
cmds.rowColumnLayout( numberOfRows=1, cs = [(30, 40)]  )
cmds.checkBox( label='Layer Override', onc = 'gm = 2', ofc = 'gm = 0')
cmds.setParent( '..' )
cmds.frameLayout( label='Disconnect Maps / Update Value ', borderStyle='out', bgc = (0.69,0.69,0.71) )
cmds.rowColumnLayout( numberOfRows=1, cs = [(30, 40)]  )
cmds.checkBox( label='Map', onc = 'mapTick = [2,3]', ofc = 'mapTick = []' )
cmds.checkBox( label='Value', onc = 'valueTick = [4,5]', ofc = 'valueTick = []'  )
cmds.setParent( '..' )
cmds.checkBox( label='Color', onc = 'cl = ".color"', ofc = 'cl = 123')
cmds.checkBox( label='Ambient Col', onc = 'cl = ".ambientColor"', ofc = 'cl = 123' )
cmds.checkBox( label='Specular Col', onc = 'cl = ".specularColor"', ofc = 'cl = 123' )
cmds.checkBox( label='Incendesence Col', onc = 'cl = ".incandescence"', ofc = 'cl = 123')
cmds.checkBox( label='Reflectivity', onc = 'cl = ".reflectivity"', ofc = 'cl = 123')
cmds.checkBox( label='Bump Depth', onc = 'cl = ".bumpDepth"', ofc = 'cl = 123')
cmds.checkBox( label='Dif Col Amount', onc = 'cl = ".diffuseColorAmount"', ofc = 'cl = 123')
cmds.checkBox( label='Reflection Col', onc = 'cl = ".reflectionColor"', ofc = 'cl = 123')
cmds.checkBox( label='Ref Col Amount', onc = 'cl = ".reflectionColorAmount"', ofc = 'cl = 123')
cmds.checkBox( label='Ref Subdivision', onc = 'cl = ".reflectionSubdivs"', ofc = 'cl = 123')
cmds.checkBox( label='Bump Value', onc = 'cl = ".bumpMult"', ofc = 'cl = 123')
cmds.checkBox( label='Refraction Col', onc = 'cl = ".refractionColor"', ofc = 'cl = 123')
cmds.checkBox( label='Refrc Col Amount', onc = 'cl = ".refractionColorAmount"', ofc = 'cl = 123')
cmds.checkBox( label='Refrc Subdivision', onc = 'cl = ".refractionSubdivs"', ofc = 'cl = 123')
cmds.setParent( '..' )
cmds.rowColumnLayout( numberOfRows=1, cs = (10,10) )
cmds.button( label = 'Disconnect Maps', command = 'chkAttrbDiscon().attrbDiscon(cl)', bgc = (0.72,0.72,0.75))
cmds.button( label = 'Pick Color Value', command = 'chkAttrbDiscon().colorWindow()', bgc = (0.72,0.85,0.85))
cmds.button( label = 'Update', command =  'chkAttrbDiscon().attrbDiscon(cl)',bgc = (0.72,0.72,0.75))
cmds.setParent( '..' )
cmds.frameLayout( label='Extra Attribute Disconnect/ Update ', w = 90, h = 120, mh= 15, borderStyle='out', bgc = (0.69,0.69,0.71))
cmds.rowColumnLayout( numberOfRows=1, cs = (10,10) )
cmds.textField('MField', ann = ' enter the shader attribute to modify. eg: < .specColor > ')
cmds.button( label = 'Update Attribute', command = 'print inputMap()', bgc = (0.72,0.72,0.75))
cmds.setParent( '..' )
cmds.rowColumnLayout( numberOfRows=1, cs = (10,10) )
cmds.textField('VField', ann = ' enter any value to update the shader attribute. eg: < 24 > ')
cmds.button( label = 'Update Value', command = 'chkAttrbDiscon().attrbDiscon(cl)',bgc = (0.72,0.72,0.75))
cmds.setParent( '..' )
cmds.setParent( '..' )
cmds.rowColumnLayout( numberOfRows=1, cs = (20,30) )
cmds.button( label = 'Blackhole', command = 'chkBlackHole().BattrbOvr()', w = 100, h = 50, bgc = (0.32,0.32,0.33))
cmds.button( label = 'Undo', command = 'cmds.undo()', w = 100, h = 50,  bgc = (0.72,0.72,0.75))
cmds.showWindow()

