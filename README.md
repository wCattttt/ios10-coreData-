# ios10-coreData-
ios10 coreData 增删该查操作

ios10马上就要更新了，其中包括CoreData的更新，CoreData提升了并发访问性能

coreData在使用上也有一些差异

在xcode7中新建项目，勾选use core data，appdelegate中的属性是：
@property (strong, nonatomic) UIWindow *window;
@property (readonly, strong, nonatomic) NSManagedObjectContext *managedObjectContext;
@property (readonly, strong, nonatomic) NSManagedObjectModel *managedObjectModel;
@property (readonly, strong, nonatomic) NSPersistentStoreCoordinator *persistentStoreCoordinator;
- (void)saveContext;
- (NSURL *)applicationDocumentsDirectory;

但在xcode8中新建项目，在勾选use core data的前提下，appdelegate中的属性：
@property (strong, nonatomic) UIWindow *window;
@property (readonly, strong) NSPersistentContainer *persistentContainer;
- (void)saveContext;

变的简洁了，数据库操作只有NSPersistentContainer *persistentContainer 这一个类了，其实xcode7中的managedObjectModel,managedObjectContext,persistentStoreCoordinator
都可以通过persistentContainer调用
managedObjectContext == persistentContainer.viewContext
managedObjectModel == persistentContainer.managedObjectModel
persistentStoreCoordinator == persistentContainer.persistentStoreCoordinator 
